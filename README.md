# Microproject-

Sure! Below is a Contact Management System in C that demonstrates the use of various conditional statements (if, if-else, switch-case) and loops (for, while, do-while).

Features of the Program:

✔ Add a new contact
✔ Display all contacts
✔ Search for a contact
✔ Delete a contact
✔ Exit the program


---

C Program: Contact Management System

#include <stdio.h>
#include <string.h>

#define MAX_CONTACTS 100

// Structure to hold contact information
struct Contact {
    char name[50];
    char phone[15];
};

// Global array to store contacts
struct Contact contacts[MAX_CONTACTS];
int contactCount = 0;

// Function Prototypes
void addContact();
void displayContacts();
void searchContact();
void deleteContact();

int main() {
    int choice;

    do {
        // Menu options
        printf("\n==== Contact Management System ====\n");
        printf("1. Add Contact\n");
        printf("2. Display Contacts\n");
        printf("3. Search Contact\n");
        printf("4. Delete Contact\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        
        switch (choice) {
            case 1:
                

C Program: Contact Management System

#include <stdio.h>
#include <string.h>

#define MAX_CONTACTS 100

// Structure to hold contact information
struct Contact {
    char name[50];
    char phone[15];
};

// Global array to store contacts
struct Contact contacts[MAX_CONTACTS];
int contactCount = 0;

// Function Prototypes
void addContact();
void displayContacts();
void searchContact();
void deleteContact();

int main() {
    int choice;

    do {
        // Menu options
        printf("\n==== Contact Management System ====\n");
        printf("1. Add Contact\n");
        printf("2. Display Contacts\n");
        printf("3. Search Contact\n");
        printf("4. Delete Contact\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        
        switch (choice) {
            case 1:
                addContact();
                break;
            case 2:
                displayContacts();
                break;
            case 3:
                searchContact();
                break;
            case 4:
                deleteContact();
                break;
            case 5:
                printf("Exiting the program...\n");
                break;
            default:
                printf("Invalid choice! Please enter a number between 1 and 5.\n");
        }
    } while (choice != 5); // Loop until the user chooses to exit

    return 0;
}

// Function to add a contact
void addContact() {
    if (contactCount < MAX_CONTACTS) {
        printf("\nEnter Name: ");
        scanf(" %[^\n]s", contacts[contactCount].name);
        printf("Enter Phone Number: ");
        scanf(" %[^\n]s", contacts[contactCount].phone);
        
        contactCount++;
        printf("Contact added successfully!\n");
    } else {
        printf("Contact list is full!\n");
    }
}

// Function to display all contacts
void displayContacts() {
    if (contactCount == 0) {
        printf("\nNo contacts available.\n");
        return;
    }

    printf("\n==== Contact List ====\n");
    for (int i = 0; i < contactCount; i++) {
        printf("%d. Name: %s, Phone: %s\n", i + 1, contacts[i].name, contacts[i].phone);
    }
}

// Function to search for a contact by name
void searchContact() {
    char searchName[50];
    int found = 0;

    if (contactCount == 0) {
        printf("\nNo contacts available.\n");
        return;
    }

    printf("\nEnter Name to Search: ");
    scanf(" %[^\n]s", searchName);

    for (int i = 0; i < contactCount; i++) {
        if (strcmp(contacts[i].name, searchName) == 0) {
            printf("Contact Found: Name: %s, Phone: %s\n", contacts[i].name, contacts[i].phone);
            found = 1;
            break;
        }
    }

    if (!found) {
        printf("Contact not found.\n");
    }
}

// Function to delete a contact by name
void deleteContact() {
    char deleteName[50];
    int index = -1;

    if (contactCount == 0) {
        printf("\nNo contacts available.\n");
        return;
    }

    printf("\nEnter Name to Delete: ");
    scanf(" %[^\n]s", deleteName);

    // Find contact index
    for (int i = 0; i < contactCount; i++) {
        if (strcmp(contacts[i].name, deleteName) == 0) {
            index = i;
            break;
        }
    }

    if (index == -1) {
        printf("Contact not found.\n");
    } else {
        // Shift contacts to remove the deleted one
        for (int i = index; i < contactCount - 1; i++) {
            contacts[i] = contacts[i + 1];
        }
        contactCount--;
        printf("Contact deleted successfully!\n");
    }
