# TodoList Mobile App
<img width="175" alt="Screenshot 2024-03-19 102932" src="https://github.com/rrrozzaq/todolist-mobile-app/assets/92041571/9584619f-cb5d-4bc9-9a77-c273b37fddd4">

## Description

## Short Description

This repository contains a mobile application for managing todo lists. The TodoList Mobile App offers features such as creating, editing, and deleting tasks, as well as setting reminders for upcoming tasks. Built with modern Android development practices, including the MVVM architecture pattern and Room Persistence Library, this app provides a clean and intuitive user experience. Explore the repository to learn more about the implementation and to clone the project for your own use. This project serves as a technical test for Software Engineer Interns.

## Cloning the Project

To clone the project, follow these steps:
1. Open a terminal window.
2. Navigate to the directory where you want to clone the project
3. Run the following command:
   ```bash
   git clone <repository-url>
    ```
Replace `<repository_url>` with the URL of this repository.

### Technical Overview

#### Architecture and Design Patterns

The project follows the MVVM (Model-View-ViewModel) architecture pattern, which separates the user interface from the business logic. This helps in maintaining clean and modular code.

#### Libraries and Dependencies

The project uses the following libraries and dependencies:

- **Room Persistence Library**: Used for managing local database operations, including CRUD (Create, Read, Update, Delete) operations on tasks.
- **ViewModel and LiveData**: Used for managing UI-related data in a lifecycle-aware manner.
- **WorkManager**: Used for scheduling and managing background tasks, such as reminder notifications for tasks.
- **Material Components**: Provides UI components and styles according to the Material Design guidelines, ensuring a modern and consistent user experience.
- **JUnit and Espresso**: Used for writing and executing unit tests and UI tests, respectively.

#### Features and Functionality

The application includes the following features:

- **List Screen**: Displays the list of tasks with options to filter tasks and navigate to the Settings screen.
- **Add Task Screen**: Allows users to add new tasks with a title, description, and due date.
- **Detail Task Screen**: Displays detailed information about a selected task, including the ability to delete the task.
- **Settings Screen**: Allows users to configure settings, such as enabling or disabling reminder notifications.
- **Notification**: Sends reminder notifications for upcoming tasks based on user preferences.

#### Best Practices

- **Separation of Concerns**: Each component of the application is responsible for a specific task, ensuring a clear separation of concerns and easier maintenance.
- **Database Operations**: Database operations are performed asynchronously using coroutines or background threads to prevent blocking the main UI thread.
- **UI Consistency**: UI components follow the Material Design guidelines, providing a consistent and intuitive user interface.
- **Error Handling**: The application handles errors gracefully and provides informative error messages to the user when necessary.
- **Testing**: The project includes both unit tests and UI tests to ensure the reliability and correctness of the codebase.

#### Code Samples

Below are snippets of code demonstrating some key aspects of the implementation:

- **Room Database Configuration**:

```java
// Database configuration
@Database(entities = {Task.class}, version = 1, exportSchema = false)
public abstract class AppDatabase extends RoomDatabase {
    public abstract TaskDao taskDao();

    private static volatile AppDatabase INSTANCE;

    public static AppDatabase getDatabase(final Context context) {
        if (INSTANCE == null) {
            synchronized (AppDatabase.class) {
                if (INSTANCE == null) {
                    INSTANCE = Room.databaseBuilder(context.getApplicationContext(),
                            AppDatabase.class, "todo_database")
                            .build();
                }
            }
        }
        return INSTANCE;
    }
}
```

- **ViewModel Implementation**:

```java
public class AddTaskViewModel extends ViewModel {
    private TaskRepository repository;

    public AddTaskViewModel(TaskRepository repository) {
        this.repository = repository;
    }

    public void insertTask(Task task) {
        repository.insert(task);
    }
}
```

### Conclusion

The TodoList Mobile App provides a convenient way to manage tasks and stay organized. With its clean architecture, robust features, and adherence to best practices, it offers a reliable solution for personal task management.
