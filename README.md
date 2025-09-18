#include <iostream>
#include <vector>
#include <string>
using namespace std;

vector<string> tasks;

void showMenu() {
    cout << "\n--- To-Do List ---" << endl;
    cout << "1. View Tasks" << endl;
    cout << "2. Add Task" << endl;
    cout << "3. Remove Task" << endl;
    cout << "4. Exit" << endl;
    cout << "Choose an option: ";
}

int main() {
    int choice;
    while (true) {
        showMenu();
        cin >> choice;
        cin.ignore(); // clear input buffer

        if (choice == 1) {
            if (tasks.empty()) {
                cout << "No tasks yet!" << endl;
            } else {
                for (int i = 0; i < tasks.size(); i++) {
                    cout << i + 1 << ". " << tasks[i] << endl;
                }
            }
        }
        else if (choice == 2) {
            string task;
            cout << "Enter a new task: ";
            getline(cin, task);
            tasks.push_back(task);
            cout << "Task added!" << endl;
        }
        else if (choice == 3) {
            int taskNum;
            cout << "Enter task number to remove: ";
            cin >> taskNum;
            if (taskNum > 0 && taskNum <= tasks.size()) {
                cout << "Removed: " << tasks[taskNum - 1] << endl;
                tasks.erase(tasks.begin() + taskNum - 1);
            } else {
                cout << "Invalid task number!" << endl;
            }
        }
        else if (choice == 4) {
            cout << "Goodbye!" << endl;
            break;
        }
        else {
            cout << "Invalid choice, try again." << endl;
        }
    }
    return 0;
}
