
#include <iostream>
#include <string>
using namespace std;

struct Book
{
    int id;
    string name;
    string author;
    bool issued;
};

int main()
{
    Book b[100];
    int total = 0;
    int choice;

    do
    {
        cout << "\n===== LIBRARY MANAGEMENT SYSTEM =====\n";
        cout << "1. Add Book\n";
        cout << "2. View Books\n";
        cout << "3. Issue Book\n";
        cout << "4. Return Book\n";
        cout << "5. Exit\n";

        cout << "Enter your choice: ";
        cin >> choice;

        if (choice == 1)
        {
            cout << "Enter Book ID: ";
            cin >> b[total].id;
            cin.ignore();

            cout << "Enter Book Name: ";
            getline(cin, b[total].name);

            cout << "Enter Author Name: ";
            getline(cin, b[total].author);

            b[total].issued = false;
            total++;

            cout << "Book added successfully!\n";
        }
        else if (choice == 2)
        {
            if (total == 0)
            {
                cout << "No books available.\n";
            }
            else
            {
                cout << "\n--- Book List ---\n";
                for (int i = 0; i < total; i++)
                {
                    cout << "ID: " << b[i].id
                         << " | Name: " << b[i].name
                         << " | Author: " << b[i].author
                         << " | Status: " << (b[i].issued ? "Issued" : "Available")
                         << endl;
                }
            }
        }
        else if (choice == 3)
        {
            int id, found = 0;
            cout << "Enter Book ID to issue: ";
            cin >> id;

            for (int i = 0; i < total; i++)
            {
                if (b[i].id == id && b[i].issued == false)
                {
                    b[i].issued = true;
                    cout << "Book issued successfully!\n";
                    found = 1;
                    break;
                }
            }

            if (!found)
                cout << "Book not available or already issued.\n";
        }
        else if (choice == 4)
        {
            int id, found = 0;
            cout << "Enter Book ID to return: ";
            cin >> id;

            for (int i = 0; i < total; i++)
            {
                if (b[i].id == id && b[i].issued == true)
                {
                    b[i].issued = false;
                    cout << "Book returned successfully!\n";
                    found = 1;
                    break;
                }
            }

            if (!found)
                cout << "Invalid Book ID or book was not issued.\n";
        }
        else if (choice == 5)
        {
            cout << "Exiting program...\n";
        }
        else
        {
            cout << "Invalid choice! Try again.\n";
        }

    } while (choice != 5);

    return 0;
}
