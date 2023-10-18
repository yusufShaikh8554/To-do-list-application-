# To-do-list-application-

#1. Task management: allow users to add, remove, and mark tasks as complete features.

class TaskManager:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({"task": task, "complete": False})

    def remove_task(self, task):
        for t in self.tasks:
            if t["task"] == task:
                self.tasks.remove(t)

    def mark_task_as_complete(self, task):
        for t in self.tasks:
            if t["task"] == task:
                t["complete"] = True

    def list_tasks(self):
        for i, task in enumerate(self.tasks):
            status = "Complete" if task["complete"] else "Incomplete"
            print(f"{i + 1}. {task['task']} - {status}")

# Example usage
task_manager = TaskManager()

while True:
    print("\nTask Manager Menu:")
    print("1. Add Task")
    print("2. Remove Task")
    print("3. Mark Task as Complete")
    print("4. List Tasks")
    print("5. Quit")

    choice = input("Enter your choice: ")

    if choice == "1":
        task = input("Enter the task: ")
        task_manager.add_task(task)
    elif choice == "2":
        task = input("Enter the task to remove: ")
        task_manager.remove_task(task)
    elif choice == "3":
        task = input("Enter the task to mark as complete: ")
        task_manager.mark_task_as_complete(task)
    elif choice == "4":
        task_manager.list_tasks()
    elif choice == "5":
        break
    else:
        print("Invalid choice. Please try again.")





#2. Task priority: implement a priority for system (e.g., High, medium, low)

class Task:
    def __init__(self, name, priority):
        self.name = name
        self.priority = priority

class PrioritySystem:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)

    def get_high_priority_tasks(self):
        return [task for task in self.tasks if task.priority == 'High']

    def get_medium_priority_tasks(self):
        return [task for task in self.tasks if task.priority == 'Medium']

    def get_low_priority_tasks(self):
        return [task for task in self.tasks if task.priority == 'Low']

# Example usage:
priority_system = PrioritySystem()
priority_system.add_task(Task("Task 1", "High"))
priority_system.add_task(Task("Task 2", "Medium"))
priority_system.add_task(Task("Task 3", "Low"))

high_priority_tasks = priority_system.get_high_priority_tasks()
medium_priority_tasks = priority_system.get_medium_priority_tasks()
low_priority_tasks = priority_system.get_low_priority_tasks()

print("High Priority Tasks:")
for task in high_priority_tasks:
    print(f"{task.name} ({task.priority})")

print("Medium Priority Tasks:")
for task in medium_priority_tasks:
    print(f"{task.name} ({task.priority})")

print("Low Priority Tasks:")
for task in low_priority_tasks:
    print(f"{task.name} ({task.priority})")



#3. Due dates: enable users to set due dates for tasks

# Create an empty dictionary to store tasks and due dates
tasks = {}

# Function to add a task with a due date
def add_task():
    task_name = input("Enter the task name: ")
    due_date = input("Enter the due date (YYYY-MM-DD): ")
    tasks[task_name] = due_date
    print("Task added!")

# Function to display all tasks and their due dates
def display_tasks():
    if tasks:
        for task, due_date in tasks.items():
            print(f"Task: {task} | Due Date: {due_date}")
    else:
        print("No tasks added yet.")

while True:
    print("\nOptions:")
    print("1. Add a task")
    print("2. Display tasks")
    print("3. Quit")
    
    choice = input("Enter your choice: ")
    
    if choice == "1":
        add_task()
    elif choice == "2":
        display_tasks()
    elif choice == "3":
        break
    else:
        print("Invalid choice. Please select 1, 2, or 3.")


#4. List view: display in a list with their details 

import tkinter as tk

# Sample data for demonstration
data = [
    {"name": "Item 1", "details": "Details for Item 1"},
    {"name": "Item 2", "details": "Details for Item 2"},
    {"name": "Item 3", "details": "Details for Item 3"},
]

def create_list_view(root, data):
    for item in data:
        label = tk.Label(root, text=f"{item['name']}: {item['details']}")
        label.pack()

if __name__ == "__main__":
    root = tk.Tk()
    root.title("List View")

    create_list_view(root, data)

    root.mainloop()



#5.Data persistence: store tasks in a file/database for Persistence across session.

# Saving tasks to a text file
def save_tasks_to_file(tasks, filename):
    with open(filename, 'w') as file:
        for task in tasks:
            file.write(task + '\n')

# Loading tasks from a text file
def load_tasks_from_file(filename):
    tasks = []
    try:
        with open(filename, 'r') as file:
            tasks = file.read().splitlines()
    except FileNotFoundError:
        pass
    return tasks

