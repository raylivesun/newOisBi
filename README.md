# NewOisBi ([wolfram/mathematics](https://www.wolframalpha.com/examples/mathematics)) 

NewOisBi is a term that seems to be related to the Open Interest Swap (OIS) and the Bank Indices Swap (Bi) in the context of fixed income markets. It could be a specific financial product or a combination of these instruments.

To provide a more detailed explanation, OIS is a type of interest rate swap where the floating leg pays interest based on the overnight rate, while the fixed leg pays a fixed rate. Bi, on the other hand, is a swap where the floating leg pays interest based on a bank index, such as LIBOR or ESTR.

NewOisBi could refer to a new financial product or a combination of OIS and Bi swaps. It might involve additional features or complexities compared to traditional OIS and Bi swaps.

If you are looking for a specific implementation or code related to NewOisBi, you would need to consult financial market data sources, financial institutions, or financial software vendors for more information.

# makefile - makefile
```makefile
CXX = g++
CXXFLAGS = -Wall -Werror -Wextra -pedantic -std=c++17 -g -fsanitize=address
LDFLAGS =  -fsanitize=address

SRC = 
OBJ = $(SRC:.cc=.o)
EXEC = newoisbi

all: $(EXEC)

$(EXEC): $(OBJ)
	$(CXX) $(LDFLAGS) -o $@ $(OBJ) $(LBLIBS)

clean:
	rm -rf $(OBJ) $(EXEC)
```

# Example c++ compiler
```c++
#include <string.h>
#include <stdio.h>
#include <stdlib.h>

#define MAX_NAME_LENGTH 20
#define MAX_SUBJECT_LENGTH 50
#define MAX_STUDENTS 100

typedef struct {
    char name[MAX_NAME_LENGTH];
    char subject[MAX_SUBJECT_LENGTH];
    int grade;
} Student;

void addStudent(Student students[], int* numStudents, const char* name, const char* subject, int grade) {
    if (*numStudents >= MAX_STUDENTS) {
        printf("Error: Maximum number of students reached.\n");
        return;
    }

    strcpy(students[*numStudents].name, name);
    strcpy(students[*numStudents].subject, subject);
    students[*numStudents].grade = grade;
    (*numStudents)++;
}

void removeStudent(Student students[], int* numStudents, int index) {
    if (index < 0 || index >= *numStudents) {
        printf("Error: Invalid student index.\n");
        return;
    }

    memmove(&students[index], &students[index + 1], (*numStudents - index - 1) * sizeof(Student));
    (*numStudents)--;
}

void displayStudents(const Student students[], int numStudents) {
    printf("Student List:\n");
    for (int i = 0; i < numStudents; i++) {
        printf("%d. %s (%s) - Grade: %d\n", i + 1, students[i].name, students[i].subject, students[i].grade);
    }
}

void sortStudentsByName(Student students[], int numStudents) {
    for (int i = 0; i < numStudents - 1; i++) {
        for (int j = 0; j < numStudents - i - 1; j++) {
            if (strcmp(students[j].name, students[j + 1].name) > 0) {
                Student temp = students[j];
                students[j] = students[j + 1];
                students[j + 1] = temp;
            }
        }
    }
}

void sortStudentsByGrade(Student students[], int numStudents) {
    for (int i = 0; i < numStudents - 1; i++) {
        for (int j = 0; j < numStudents - i - 1; j++) {
            if (students[j].grade < students[j + 1].grade) {
                Student temp = students[j];
                students[j] = students[j + 1];
                students[j + 1] = temp;
            }
        }
    }
}

int main() {
    Student students[MAX_STUDENTS];
    int numStudents = 0;

    while (1) {
        printf("\nStudent Management System\n");
        printf("1. Add Student\n");
        printf("2. Remove Student\n");
        printf("3. Display Students\n");
        printf("4. Sort Students by Name\n");
        printf("5. Sort Students by Grade\n");
        printf("6. Exit\n");
        printf("Enter your choice: ");

        int choice;
        scanf("%d", &choice);

        switch (choice) {
            case 1: {
                char name[MAX_NAME_LENGTH];
                char subject[MAX_SUBJECT_LENGTH];
                int grade;

                printf("Enter student name: ");
                scanf("%s", name);
                printf("Enter student subject: ");
                scanf("%s", subject);
                printf("Enter student grade: ");
                scanf("%d", & grade);
                addStudent(students, &numStudents, name, subject, grade);
                break;

            case 2: {
                int index;
                printf("Enter student index to remove: ");
                scanf("%d", &index);
                removeStudent(students, &numStudents, index - 1);
                break;

            case 3:
            displayStudents(students, numStudents);
            break;
            case 4:
            sortStudentsByName(students, numStudents);
            displayStudents(students, numStudents);
            break;
            case 5:
            sortStudentsByGrade(students, numStudents);
            displayStudents(students, numStudents);
            break;
            case 6:
            return 0;
            default:
            printf("Invalid choice. Please try again.\n");
            }
            }
        }
        printf("\n");
        system("pause");
        system("cls");
    }
    return 0;
}
```
# install makefile
$-> make all    


        