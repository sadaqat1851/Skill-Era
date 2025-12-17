# SKILL ERA - E-LEARNING PLATFORM
## PROJECT REPORT

---

**Course:** CSC241 – Object Oriented Programming  
**Instructor:** Dr. Rizwan Rashid  
**Department:** Computer Science  
**Institution:** COMSATS University, Islamabad  
**Semester:** Fall 2025  

---

## PROJECT TEAM

| Role | Name | Responsibilities |
|------|------|------------------|
| Team Lead | Muzammil Ghaffar | Project coordination, GUI development (Login & Admin Dashboard), Data persistence, Project integration |
| Member 2 | Muhammad Zaeem | Model classes development (User, Student hierarchy), OOP concepts implementation, Core business logic |
| Member 3 | Sadaqat Hussain | Student Dashboard GUI, User interaction features, Progress tracking & Certificate generation |
| Member 4 | Ahsan Raza | Course & Quiz management, Data validation, File handling & Assignment submission system |

---

## 1. INTRODUCTION

Skill Era is a comprehensive e-learning management system designed to facilitate online education through an intuitive graphical user interface. The platform bridges the gap between instructors and students by providing a centralized system for course management, learning materials distribution, assessment, and progress tracking. In today's digital age, where online education has become essential, Skill Era offers a robust solution that enables students to enroll in courses, access video lectures, take quizzes, submit assignments, and earn certificates upon completion. The system also empowers administrators with tools to create and manage courses efficiently. Built entirely in Java using Swing for the GUI, Skill Era demonstrates the practical application of object-oriented programming principles to solve real-world educational challenges.

---

## 2. TASK DISTRIBUTION

### Muzammil Ghaffar (Team Lead)
- Developed the authentication system (LoginFrame.java)
- Implemented the Admin Dashboard with course creation functionality
- Designed and implemented the data persistence layer (DataManager.java, DataBundle.java)
- Coordinated team efforts and ensured project integration
- Managed file serialization and deserialization
- Handled project submission and documentation

### Muhammad Zaeem
- Designed the abstract User class hierarchy
- Implemented the Student class with inheritance
- Developed the Progress inner class for tracking student achievements
- Implemented core OOP concepts: encapsulation, inheritance, abstraction
- Created the Course model class with proper encapsulation
- Implemented validation logic for user credentials

### Sadaqat Hussain
- Developed the Student Dashboard interface (StudentDashboard.java)
- Implemented course browsing and enrollment features
- Created the video watching functionality with progress tracking
- Developed the progress viewing system
- Implemented the certificate generation and viewing feature
- Designed the completed courses tracking mechanism

### Ahsan Raza
- Developed the QuizQuestion class
- Implemented the quiz-taking functionality with scoring
- Created the assignment submission system
- Developed file handling for assignment storage
- Implemented data validation for course creation
- Created the formatting for assignment files and certificates

---

## 3. FEATURES OF THE SYSTEM

### 3.1 User Management
- **User Registration**: New students can register with username, password, and email
- **Secure Login**: Authentication system with password verification
- **Role-Based Access**: Separate interfaces for students and administrators
- **Admin Creation**: First registered admin gets administrative privileges
- **User Validation**: Prevents duplicate usernames and empty fields

### 3.2 Course Management
- **Course Creation**: Admins can create courses with multiple components
- **Video Lectures**: Support for multiple YouTube video links per course
- **Quiz System**: Multiple-choice questions with automatic grading
- **Assignments**: Text-based assignment prompts and submissions
- **Course Information**: Display of course code, title, and instructor details

### 3.3 Student Features
- **Course Browsing**: View all available courses in the system
- **Enrollment**: Easy one-click enrollment in courses
- **Video Access**: Watch course videos directly from the dashboard
- **Quiz Taking**: Interactive quiz interface with instant scoring
- **Assignment Submission**: Submit assignments with automatic file saving
- **Progress Tracking**: Real-time progress monitoring (0-100%)
- **Certificate Generation**: Automatic certificate upon 100% completion
- **Completed Courses View**: Track all completed courses with certificate IDs

### 3.4 Admin Features
- **Course Creation**: Create courses with videos, quizzes, and assignments
- **Student Management**: View all registered students
- **Enrollment Tracking**: See which courses students are enrolled in
- **Student Removal**: Delete student accounts if needed
- **Course Listing**: View all created courses

### 3.5 Data Persistence
- **Serialization**: All data saved using Java serialization
- **Automatic Save**: Data persists across application sessions
- **Text Snapshots**: Human-readable text file for data verification
- **Assignment Files**: Individual files for each assignment submission

### 3.6 Progress System
- **Video Completion**: 33% progress upon watching videos
- **Quiz Completion**: 66% progress upon completing quiz
- **Assignment Submission**: 100% progress upon assignment submission
- **Certificate Eligibility**: Certificate available at 100% completion
- **Verification ID**: Unique 10-character alphanumeric certificate ID

---

## 4. CLASS DIAGRAM

```
┌─────────────────────────────────────────────────────────────────┐
│                          <<interface>>                          │
│                         Serializable                            │
└─────────────────────────────────────────────────────────────────┘
                                  △
                                  │ implements
                                  │
┌─────────────────────────────────────────────────────────────────┐
│                     <<abstract class>>                          │
│                            User                                 │
├─────────────────────────────────────────────────────────────────┤
│ # username: String                                              │
│ # password: String                                              │
│ # email: String                                                 │
├─────────────────────────────────────────────────────────────────┤
│ + getUsername(): String                                         │
│ + setUsername(String): void                                     │
│ + getPassword(): String                                         │
│ + setPassword(String): void                                     │
│ + getEmail(): String                                            │
│ + setEmail(String): void                                        │
│ + showDashboard(): void <<abstract>>                            │
│ + equals(Object): boolean                                       │
│ + hashCode(): int                                               │
│ + toString(): String                                            │
└─────────────────────────────────────────────────────────────────┘
                                  △
                                  │ extends
                                  │
┌─────────────────────────────────────────────────────────────────┐
│                           Student                               │
├─────────────────────────────────────────────────────────────────┤
│ - enrolledCourses: ArrayList<Course>                            │
│ - progressByCourse: Map<String, Progress>                       │
│ - admin: boolean                                                │
├─────────────────────────────────────────────────────────────────┤
│ + Student(String, String, String)                               │
│ + Student(String, String, String, boolean)                      │
│ + getEnrolledCourses(): ArrayList<Course>                       │
│ + enrollInCourse(Course): void                                  │
│ + getProgress(String): Progress                                 │
│ + isAdmin(): boolean                                            │
│ + updateProgress(...): void                                     │
│ + showDashboard(): void                                         │
│                                                                 │
│ ┌─────────────────────────────────────────────────────────┐   │
│ │            <<inner class>>                              │   │
│ │               Progress                                  │   │
│ ├─────────────────────────────────────────────────────────┤   │
│ │ - progressPercent: int                                  │   │
│ │ - quizCompleted: boolean                                │   │
│ │ - assignmentSubmitted: boolean                          │   │
│ │ - videoCompleted: boolean                               │   │
│ │ - certificateId: String                                 │   │
│ ├─────────────────────────────────────────────────────────┤   │
│ │ + getProgressPercent(): int                             │   │
│ │ + setProgressPercent(int): void                         │   │
│ │ + isVideoCompleted(): boolean                           │   │
│ │ + setVideoCompleted(boolean): void                      │   │
│ │ + isQuizCompleted(): boolean                            │   │
│ │ + setQuizCompleted(boolean): void                       │   │
│ │ + isAssignmentSubmitted(): boolean                      │   │
│ │ + setAssignmentSubmitted(boolean): void                 │   │
│ │ + getCertificateId(): String                            │   │
│ │ + setCertificateId(String): void                        │   │
│ └─────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
           1                                          *
           │ enrolls in                               │
           │◇────────────────────────────────────────▷│
           │                                          │
┌─────────────────────────────────────────────────────────────────┐
│                          Course                                 │
├─────────────────────────────────────────────────────────────────┤
│ - courseCode: String                                            │
│ - courseTitle: String                                           │
│ - instructorName: String                                        │
│ - videoLinks: ArrayList<String>                                 │
│ - quizQuestions: ArrayList<QuizQuestion>                        │
│ - assignmentPrompts: ArrayList<String>                          │
│ - certificateNote: String                                       │
├─────────────────────────────────────────────────────────────────┤
│ + Course(String, String, String)                                │
│ + Course(String, String, String, List, List, List, String)      │
│ + getCourseCode(): String                                       │
│ + setCourseCode(String): void                                   │
│ + getCourseTitle(): String                                      │
│ + setCourseTitle(String): void                                  │
│ + getInstructorName(): String                                   │
│ + setInstructorName(String): void                               │
│ + getVideoLinks(): List<String>                                 │
│ + setVideoLinks(List<String>): void                             │
│ + getQuizQuestions(): List<QuizQuestion>                        │
│ + setQuizQuestions(List<QuizQuestion>): void                    │
│ + getAssignmentPrompts(): List<String>                          │
│ + setAssignmentPrompts(List<String>): void                      │
│ + getCertificateNote(): String                                  │
│ + setCertificateNote(String): void                              │
│ + equals(Object): boolean                                       │
│ + hashCode(): int                                               │
│ + toString(): String                                            │
└─────────────────────────────────────────────────────────────────┘
                                  │ composition
                                  │ contains
                                  ▼
┌─────────────────────────────────────────────────────────────────┐
│                        QuizQuestion                             │
├─────────────────────────────────────────────────────────────────┤
│ - question: String                                              │
│ - options: ArrayList<String>                                    │
│ - correctIndex: int                                             │
├─────────────────────────────────────────────────────────────────┤
│ + QuizQuestion(String, List<String>, int)                       │
│ + getQuestion(): String                                         │
│ + getOptions(): List<String>                                    │
│ + getCorrectIndex(): int                                        │
└─────────────────────────────────────────────────────────────────┘


┌─────────────────────────────────────────────────────────────────┐
│                         DataBundle                              │
├─────────────────────────────────────────────────────────────────┤
│ - users: ArrayList<User>                                        │
│ - courses: ArrayList<Course>                                    │
├─────────────────────────────────────────────────────────────────┤
│ + DataBundle(ArrayList<User>, ArrayList<Course>)                │
│ + getUsers(): ArrayList<User>                                   │
│ + getCourses(): ArrayList<Course>                               │
└─────────────────────────────────────────────────────────────────┘
                                  △
                                  │ uses
                                  │
┌─────────────────────────────────────────────────────────────────┐
│                        DataManager                              │
├─────────────────────────────────────────────────────────────────┤
│ - DATA_FILE: String = "skillera_data.dat"                       │
├─────────────────────────────────────────────────────────────────┤
│ + saveData(ArrayList<User>, ArrayList<Course>): void            │
│ + loadData(): DataBundle                                        │
│ - writeTextSnapshot(ArrayList<User>, ArrayList<Course>): void   │
└─────────────────────────────────────────────────────────────────┘


GUI CLASSES (extends JFrame, implements ActionListener)
═══════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────────────┐
│                        LoginFrame                               │
├─────────────────────────────────────────────────────────────────┤
│ - users: ArrayList<User>                                        │
│ - courses: ArrayList<Course>                                    │
│ - dataManager: DataManager                                      │
│ - loginUsernameField: JTextField                                │
│ - loginPasswordField: JPasswordField                            │
│ - registerUsernameField: JTextField                             │
│ - registerPasswordField: JPasswordField                         │
│ - registerEmailField: JTextField                                │
│ - roleBox: JComboBox<String>                                    │
│ - loginButton: JButton                                          │
│ - registerButton: JButton                                       │
├─────────────────────────────────────────────────────────────────┤
│ + LoginFrame(ArrayList<User>, ArrayList<Course>, DataManager)   │
│ - buildUi(): void                                               │
│ - buildLoginPanel(): JPanel                                     │
│ - buildRegisterPanel(): JPanel                                  │
│ - attachEvents(): void                                          │
│ + actionPerformed(ActionEvent): void                            │
│ - handleLogin(): void                                           │
│ - handleRegister(): void                                        │
│ - findUser(String): User                                        │
│ - findUser(String, String): User                                │
│ - openDashboard(User): void                                     │
│ - clearFields(): void                                           │
│ - hasAdmin(): boolean                                           │
└─────────────────────────────────────────────────────────────────┘


┌─────────────────────────────────────────────────────────────────┐
│                     StudentDashboard                            │
├─────────────────────────────────────────────────────────────────┤
│ - student: Student                                              │
│ - courses: ArrayList<Course>                                    │
│ - users: ArrayList<User>                                        │
│ - dataManager: DataManager                                      │
│ - courseList: JList<Course>                                     │
│ - courseListModel: DefaultListModel<Course>                     │
│ - courseDetails: JTextArea                                      │
│ - watchVideosButton: JButton                                    │
│ - takeQuizButton: JButton                                       │
│ - submitAssignmentButton: JButton                               │
│ - viewProgressButton: JButton                                   │
│ - viewCertificateButton: JButton                                │
│ - viewCompletedButton: JButton                                  │
│ - browseCoursesButton: JButton                                  │
├─────────────────────────────────────────────────────────────────┤
│ + StudentDashboard(Student, ArrayList, ArrayList, DataManager)  │
│ - buildUi(): void                                               │
│ - attachEvents(): void                                          │
│ - showCourse(Course): void                                      │
│ + actionPerformed(ActionEvent): void                            │
│ - browseCourses(): void                                         │
│ - watchVideos(Course): void                                     │
│ - takeQuiz(Course): void                                        │
│ - submitAssignment(Course): void                                │
│ - saveAssignmentToFile(Student, Course, String): void           │
│ - viewProgress(Course): void                                    │
│ - viewCertificate(Course): void                                 │
│ - generateCertificateId(): String                               │
│ - viewCompletedCourses(): void                                  │
│ - ensureEnrolled(Course): boolean                               │
│ - openLink(String): void                                        │
└─────────────────────────────────────────────────────────────────┘


┌─────────────────────────────────────────────────────────────────┐
│                      AdminDashboard                             │
├─────────────────────────────────────────────────────────────────┤
│ - users: ArrayList<User>                                        │
│ - courses: ArrayList<Course>                                    │
│ - dataManager: DataManager                                      │
│ - codeField: JTextField                                         │
│ - titleField: JTextField                                        │
│ - instructorField: JTextField                                   │
│ - videosArea: JTextArea                                         │
│ - quizArea: JTextArea                                           │
│ - assignmentsArea: JTextArea                                    │
│ - certificateField: JTextField                                  │
│ - addCourseButton: JButton                                      │
│ - courseListModel: DefaultListModel<Course>                     │
│ - courseList: JList<Course>                                     │
│ - studentListModel: DefaultListModel<Student>                   │
│ - studentList: JList<Student>                                   │
│ - viewEnrolledButton: JButton                                   │
│ - deleteStudentButton: JButton                                  │
├─────────────────────────────────────────────────────────────────┤
│ + AdminDashboard(Student, ArrayList, ArrayList, DataManager)    │
│ - buildUi(): void                                               │
│ - labeled(String, JTextField): JPanel                           │
│ - labeledArea(String, JTextArea): JPanel                        │
│ - attachEvents(): void                                          │
│ + actionPerformed(ActionEvent): void                            │
│ - handleAddCourse(): void                                       │
│ - handleDeleteStudent(): void                                   │
│ - handleViewEnrolled(): void                                    │
│ - parseLines(String): List<String>                              │
│ - parseQuiz(String): List<QuizQuestion>                         │
│ - clearForm(): void                                             │
└─────────────────────────────────────────────────────────────────┘


RELATIONSHIPS
═════════════════════════════════════════════════════════════

1. INHERITANCE:
   - Student extends User (abstract class)
   - User implements Serializable
   - All model classes implement Serializable

2. COMPOSITION:
   - Course HAS-A QuizQuestion (strong ownership)
   - Student HAS-A Progress (inner class, strong ownership)

3. AGGREGATION:
   - Student HAS-MANY Course (weak relationship via enrollment)
   - DataBundle HAS-MANY User
   - DataBundle HAS-MANY Course

4. ASSOCIATION:
   - LoginFrame uses DataManager
   - StudentDashboard uses Student, Course, DataManager
   - AdminDashboard uses Student, Course, DataManager

5. DEPENDENCY:
   - GUI classes depend on model classes
   - All classes depend on DataManager for persistence
```

---

## 5. OOP CONCEPTS IMPLEMENTATION

### 5.1 Encapsulation
**Definition**: Encapsulation is the bundling of data and methods that operate on that data within a single unit (class), while restricting direct access to some components.

**Implementation in Skill Era**:

1. **Private Data Members**: All class attributes are declared private
```java
// In User class
private String username;
private String password;
private String email;

// In Course class
private String courseCode;
private ArrayList<QuizQuestion> quizQuestions;
```

2. **Public Getters and Setters**: Controlled access through methods
```java
public String getUsername() {
    return username;
}

public void setUsername(String username) {
    this.username = username;
}
```

3. **Protected Access**: In abstract User class for subclass access
```java
protected String username;  // Accessible in Student subclass
```

**Benefits Demonstrated**:
- Data hiding prevents direct manipulation of sensitive information (passwords)
- Validation can be added in setters
- Internal representation can change without affecting external code

### 5.2 Inheritance
**Definition**: Inheritance allows a class to inherit properties and methods from another class, promoting code reuse and establishing hierarchical relationships.

**Implementation in Skill Era**:

```java
// Abstract superclass
public abstract class User implements Serializable {
    protected String username;
    protected String password;
    protected String email;
    
    public abstract void showDashboard();
}

// Concrete subclass
public class Student extends User {
    private ArrayList<Course> enrolledCourses;
    private boolean admin;
    
    @Override
    public void showDashboard() {
        System.out.println("Welcome, " + username);
    }
}
```

**Hierarchy**:
- User (abstract parent) → Student (concrete child)
- Student inherits: username, password, email, and their getters/setters
- Student adds: enrolledCourses, admin status, progress tracking

**Benefits Demonstrated**:
- Code reuse: Student doesn't redefine common user properties
- Polymorphism: User references can point to Student objects
- Extensibility: Easy to add more user types (e.g., Instructor)

### 5.3 Abstraction
**Definition**: Abstraction hides complex implementation details and shows only essential features, allowing focus on what an object does rather than how it does it.

**Implementation in Skill Era**:

1. **Abstract Class with Abstract Method**:
```java
public abstract class User implements Serializable {
    public abstract void showDashboard();
}
```

2. **Interface Implementation**:
```java
public class User implements Serializable {
    // Must implement serialization behavior
}
```

3. **Hiding Implementation Details**:
- DataManager hides file I/O complexity
- Users of DataManager only need to call `saveData()` or `loadData()`
- Internal serialization mechanism is hidden

**Benefits Demonstrated**:
- Simplified interface: GUI classes don't worry about file formats
- Flexibility: Can change from serialization to database without affecting GUI
- Forced implementation: Subclasses must implement showDashboard()

### 5.4 Polymorphism
**Definition**: Polymorphism allows objects of different classes to be treated as objects of a common superclass, enabling one interface to be used for different data types.

**Implementation in Skill Era**:

1. **Method Overriding**:
```java
// In User class
@Override
public String toString() {
    return username;
}

// In Course class
@Override
public String toString() {
    return courseCode + " - " + courseTitle;
}
```

2. **Runtime Polymorphism**:
```java
ArrayList<User> users = new ArrayList<>();
users.add(new Student("john", "pass", "john@mail.com"));

for (User u : users) {
    u.showDashboard();  // Calls Student's implementation
}
```

3. **Constructor Overloading**:
```java
public Student(String username, String password, String email) {
    // Regular student
}

public Student(String username, String password, String email, boolean admin) {
    // Admin student
}
```

**Benefits Demonstrated**:
- Flexibility: One collection holds different user types
- Dynamic method dispatch: Correct method called at runtime
- Code reusability: Same method signature, different behaviors

### 5.5 Composition and Aggregation

**Composition** (Strong ownership - "has-a" relationship where part cannot exist without whole):
```java
// Course HAS-A QuizQuestion
public class Course {
    private ArrayList<QuizQuestion> quizQuestions;
}
// If Course is deleted, its QuizQuestions are deleted

// Student HAS-A Progress (inner class)
public class Student {
    public static class Progress {
        private int progressPercent;
    }
}
```

**Aggregation** (Weak ownership - parts can exist independently):
```java
// Student HAS-MANY Course (via enrollment)
public class Student {
    private ArrayList<Course> enrolledCourses;
}
// If Student is deleted, Courses still exist
```

### 5.6 Additional OOP Features

**Inner Class**:
```java
public class Student extends User {
    public static class Progress implements Serializable {
        // Progress is tightly coupled with Student
    }
}
```

**Collections Framework**:
- ArrayList for dynamic collections
- HashMap for key-value progress tracking

**Exception Handling**:
```java
try {
    int chosen = Integer.parseInt(answer.trim()) - 1;
} catch (Exception ignored) {}
```

---

## 6. CODE AND SCREENSHOTS

### 6.1 Main Class
**File**: Main.java  
**Purpose**: Application entry point that initializes the system

```java
import gui.LoginFrame;
import models.Course;
import models.User;
import persistence.DataManager;
import persistence.DataBundle;
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        DataManager dataManager = new DataManager();
        DataBundle bundle = dataManager.loadData();

        ArrayList<User> users = bundle.getUsers();
        ArrayList<Course> courses = bundle.getCourses();

        if (users == null) {
            users = new ArrayList<>();
        }
        if (courses == null) {
            courses = new ArrayList<>();
        }

        new LoginFrame(users, courses, dataManager);
    }
}
```

**Explanation**: The Main class loads existing data from persistent storage and launches the login interface. It initializes empty collections if no data exists, ensuring a smooth first-time startup.

---

### 6.2 Model Classes

#### User Class (Abstract)
**File**: models/User.java  
**Purpose**: Abstract base class for all users

```java
package models;

import java.io.Serializable;

public abstract class User implements Serializable {
    private static final long serialVersionUID = 1L;

    protected String username;
    protected String password;
    protected String email;

    protected User(String username, String password, String email) {
        this.username = username;
        this.password = password;
        this.email = email;
    }

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public abstract void showDashboard();

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        User other = (User) obj;
        return username != null && username.equals(other.username);
    }

    @Override
    public int hashCode() {
        return username == null ? 0 : username.hashCode();
    }

    @Override
    public String toString() {
        return username;
    }
}
```

**Key Features**:
- Abstract class implementing Serializable for persistence
- Protected fields accessible to subclasses
- Abstract method `showDashboard()` forces implementation
- Proper equals() and hashCode() implementation

---

#### Student Class
**File**: models/Student.java  
**Purpose**: Represents a student user with course enrollment and progress tracking

```java
package models;

import java.io.Serializable;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Map;

public class Student extends User {
    private static final long serialVersionUID = 1L;

    private ArrayList<Course> enrolledCourses;
    private Map<String, Progress> progressByCourse;
    private boolean admin;

    public Student(String username, String password, String email) {
        this(username, password, email, false);
    }

    public Student(String username, String password, String email, boolean admin) {
        super(username, password, email);
        this.enrolledCourses = new ArrayList<>();
        this.progressByCourse = new HashMap<>();
        this.admin = admin;
    }

    public ArrayList<Course> getEnrolledCourses() {
        return enrolledCourses;
    }

    public void enrollInCourse(Course course) {
        if (course == null) return;
        if (!enrolledCourses.contains(course)) {
            enrolledCourses.add(course);
            progressByCourse.put(course.getCourseCode(), new Progress());
        }
    }

    public Progress getProgress(String courseCode) {
        return progressByCourse.get(courseCode);
    }

    public boolean isAdmin() {
        return admin;
    }

    public void updateProgress(String courseCode, int percent, 
                              boolean quizDone, boolean assignmentDone, 
                              boolean videoDone) {
        Progress progress = progressByCourse.get(courseCode);
        if (progress == null) {
            progress = new Progress();
            progressByCourse.put(courseCode, progress);
        }
        progress.setProgressPercent(Math.max(progress.getProgressPercent(), percent));
        if (quizDone) progress.setQuizCompleted(true);
        if (assignmentDone) progress.setAssignmentSubmitted(true);
        if (videoDone) progress.setVideoCompleted(true);
    }

    @Override
    public void showDashboard() {
        System.out.println("Welcome, " + username + "! Student dashboard coming up.");
    }

    public static class Progress implements Serializable {
        private static final long serialVersionUID = 1L;
        private int progressPercent;
        private boolean quizCompleted;
        private boolean assignmentSubmitted;
        private boolean videoCompleted;
        private String certificateId;

        public int getProgressPercent() { return progressPercent; }
        public void setProgressPercent(int progressPercent) {
            this.progressPercent = Math.max(0, Math.min(100, progressPercent));
        }
        
        public boolean isVideoCompleted() { return videoCompleted; }
        public void setVideoCompleted(boolean videoCompleted) {
            this.videoCompleted = videoCompleted;
        }
        
        public boolean isQuizCompleted() { return quizCompleted; }
        public void setQuizCompleted(boolean quizCompleted) {
            this.quizCompleted = quizCompleted;
        }
        
        public boolean isAssignmentSubmitted() { return assignmentSubmitted; }
        public void setAssignmentSubmitted(boolean assignmentSubmitted) {
            this.assignmentSubmitted = assignmentSubmitted;
        }
        
        public String getCertificateId() { return certificateId; }
        public void setCertificateId(String certificateId) {
            this.certificateId = certificateId;
        }
    }
}
```

**Key Features**:
- Extends User abstract class
- Inner Progress class for tight coupling
- HashMap for O(1) progress lookup by course code
- Admin flag for role-based access
- Progress validation (0-100%)

---

#### Course Class
**File**: models/Course.java

```java
package models;

import java.io.Serializable;
import java.util.ArrayList;
import java.util.List;

public class Course implements Serializable {
    private static final long serialVersionUID = 1L;

    private String courseCode;
    private String courseTitle;
    private String instructorName;
    private ArrayList<String> videoLinks;
    private ArrayList<QuizQuestion> quizQuestions;
    private ArrayList<String> assignmentPrompts;
    private String certificateNote;

    public Course(String courseCode, String courseTitle, String instructorName) {
        this(courseCode, courseTitle, instructorName, 
             new ArrayList<>(), new ArrayList<>(), new ArrayList<>(), null);
    }

    public Course(String courseCode, String courseTitle, String instructorName,
                  List<String> videoLinks, List<QuizQuestion> quizQuestions,
                  List<String> assignmentPrompts, String certificateNote) {
        this.courseCode = courseCode;
        this.courseTitle = courseTitle;
        this.instructorName = instructorName;
        this.videoLinks = videoLinks == null ? new ArrayList<>() : 
                         new ArrayList<>(videoLinks);
        this.quizQuestions = quizQuestions == null ? new ArrayList<>() : 
                            new ArrayList<>(quizQuestions);
        this.assignmentPrompts = assignmentPrompts == null ? new ArrayList<>() : 
                                new ArrayList<>(assignmentPrompts);
        this.certificateNote = certificateNote;
    }

    // Getters and setters with defensive copying
    public List<String> getVideoLinks() {
        return videoLinks == null ? new ArrayList<>() : new ArrayList<>(videoLinks);
    }

    public List<QuizQuestion> getQuizQuestions() {
        return quizQuestions == null ? new ArrayList<>() : 
               new ArrayList<>(quizQuestions);
    }

    @Override
    public String toString() {
        return courseCode + " - " + courseTitle + " (" + instructorName + ")";
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Course other = (Course) obj;
        return courseCode != null && 
               courseCode.equalsIgnoreCase(other.courseCode);
    }
}
```

**Key Features**:
- Composition relationship with QuizQuestion
- Defensive copying in getters prevents external modification
- Constructor overloading for flexibility
- Case-insensitive course code comparison

---

#### QuizQuestion Class
**File**: models/QuizQuestion.java

```java
package models;

import java.io.Serializable;
import java.util.ArrayList;
import java.util.List;

public class QuizQuestion implements Serializable {
    private static final long serialVersionUID = 1L;

    private String question;
    private ArrayList<String> options;
    private int correctIndex;

    public QuizQuestion(String question, List<String> options, int correctIndex) {
        this.question = question;
        this.options = options == null ? new ArrayList<>() : 
                      new ArrayList<>(options);
        this.correctIndex = Math.max(0, Math.min(2, correctIndex));
    }

    public String getQuestion() {
        return question;
    }

    public List<String> getOptions() {
        return new ArrayList<>(options);
    }

    public int getCorrectIndex() {
        return correctIndex;
    }
}
```

**Key Features**:
- Immutable design (no setters)
- Validation of correctIndex (0-2 range)
- Defensive copying

---

### 6.3 Persistence Layer

#### DataBundle Class
**File**: persistence/DataBundle.java

```java
package persistence;

import models.Course;
import models.User;
import java.io.Serializable;
import java.util.ArrayList;

public class DataBundle implements Serializable {
    private static final long serialVersionUID = 1L;
    private ArrayList<User> users;
    private ArrayList<Course> courses;

    public DataBundle(ArrayList<User> users, ArrayList<Course> courses) {
        this.users = users;
        this.courses = courses;
    }

    public ArrayList<User> getUsers() {
        return users;
    }

    public ArrayList<Course> getCourses() {
        return courses;
    }
}
```

**Purpose**: Wrapper class for serializing multiple collections together

---

#### DataManager Class
**File**: persistence/DataManager.java  
**Purpose**: Handles all file I/O operations

**Key Methods**:
- `saveData()`: Serializes users and courses to binary file
- `loadData()`: Deserializes data from file
- `writeTextSnapshot()`: Creates human-readable backup

**Benefits**:
- Centralized persistence logic
- Automatic backup creation
- Error handling and recovery
- Debug logging

---

### 6.4 GUI Classes

#### LoginFrame
**File**: gui/LoginFrame.java  
**Features**:
- Tabbed interface for login and registration
- Input validation
- Admin role management (only one admin allowed)
- Password masking with JPasswordField
- Automatic dashboard routing based on role

**Screenshot Description**:
Login screen shows two tabs: "Login" and "Register". Login tab has username and password fields with a login button. Register tab adds email field and role selection dropdown.

---

#### StudentDashboard
**File**: gui/StudentDashboard.java  
**Features**:
- Course list on the left, details on the right
- Browse and enroll in new courses
- Watch videos (opens in browser)
- Take quizzes with instant scoring
- Submit assignments (saves to file)
- View progress breakdown
- Generate and view certificates
- View all completed courses

**Screenshot Description**:
Main dashboard shows enrolled courses in a JList on the left. Selected course details appear in a JTextArea on the right showing videos, quiz questions, and assignments. Bottom panel has action buttons.

---

#### AdminDashboard
**File**: gui/AdminDashboard.java  
**Features**:
- Form-based course creation
- Video URL input (one per line)
- Quiz creation with special format: `Question|Opt1|Opt2|Opt3|CorrectAnswer`
- Assignment prompt input
- Student list view
- View student enrollments
- Delete students
- Live course list

**Screenshot Description**:
Left side shows input fields for course creation. Right side shows two lists: created courses above and registered students below with management buttons.

---

## 7. SYSTEM WORKFLOW

### 7.1 First-Time User Flow
1. Application starts → Main.java loads data
2. No data exists → Empty lists created
3. LoginFrame appears with Register tab
4. User fills registration form (username, password, email, role)
5. If role = Admin: Becomes first admin
6. If role = Student: Regular student created
7. Data saved to skillera_data.dat
8. User can now login

### 7.2 Student Workflow
1. Login with credentials
2. StudentDashboard opens
3. Click "Browse All Courses" → View available courses
4. Select course → Click "Enroll"
5. Course added to "My Courses" list
6. Select enrolled course → Course details shown
7. **Watch Videos** → Opens in browser → Mark as watched (33%)
8. **Take Quiz** → Answer questions → Get score → Progress to 66%
9. **Submit Assignment** → Type answer → Saved to file → Progress to 100%
10. **View Certificate** → Shows certificate with unique ID
11. **My Completed Courses** → View all 100% courses

### 7.3 Admin Workflow
1. Login as admin
2. AdminDashboard opens
3. Fill course creation form:
   - Course Code: CS101
   - Course Title: Intro to Programming
   - Instructor: Dr. Smith
   - Videos: YouTube URLs (one per line)
   - Quiz: `What is a variable?|Storage|Function|Loop|1`
   - Assignments: Problem statements
4. Click "Create Course"
5. Course added to system
6. All students can now browse and enroll
7. View students → See enrollments
8. Delete problematic users if needed

---

## 8. TECHNICAL IMPLEMENTATION DETAILS

### 8.1 Data Persistence
- **Format**: Java Object Serialization
- **File**: skillera_data.dat (binary)
- **Backup**: skillera_data.txt (human-readable)
- **Assignment Storage**: assignments/ folder with timestamped files

### 8.2 Progress Tracking Algorithm
```
If watch videos → progress = max(current, 33%)
If complete quiz → progress = max(current, 66%)
If submit assignment → progress = 100%
```

### 8.3 Certificate Generation
- Automatic generation when progress = 100%
- 10-character alphanumeric ID (uppercase + digits)
- Persistent across sessions
- Displayed in formatted ASCII art

### 8.4 File Naming Convention
Assignment files: `{username}_{courseCode}_{timestamp}.txt`  
Example: `Sadaqat_OOP104_20251217_192053.txt`

---

## 9. VALIDATION AND ERROR HANDLING

### 9.1 Input Validation
- Empty field checks (username, password, email)
- Duplicate username prevention
- Course code uniqueness verification
- Quiz answer range validation (1-3)
- Progress bounds checking (0-100%)

### 9.2 Error Recovery
- Missing data file → Create empty collections
- Corrupted file → Log error, return defaults
- Invalid quiz format → Use default correct answer
- File write errors → User notification

---

## 10. FUTURE ENHANCEMENTS

1. **Database Integration**: Replace serialization with SQL database
2. **Password Encryption**: Hash passwords for security
3. **Email Verification**: Send confirmation emails
4. **Advanced Quizzes**: Multiple correct answers, different question types
5. **Video Integration**: Embedded video player instead of browser
6. **Discussion Forums**: Student interaction features
7. **Grade Analytics**: Statistical analysis of student performance
8. **Mobile App**: Android/iOS companion app
9. **Live Classes**: Video conferencing integration
10. **Content Recommendations**: AI-based course suggestions

---

## 11. CONCLUSION

Skill Era successfully demonstrates the application of object-oriented programming principles to create a fully functional e-learning management system. The project effectively utilizes encapsulation to protect data integrity, inheritance to promote code reuse, abstraction to simplify complex operations, and polymorphism to enable flexible design. Through the development of this system, our team gained practical experience in collaborative software development, GUI design with Java Swing, file I/O operations, and the implementation of comprehensive business logic. The modular architecture ensures that the system is maintainable, extensible, and adheres to software engineering best practices. Skill Era stands as a testament to the power of OOP in solving real-world problems and provides a solid foundation for future enhancements in the e-learning domain.

---

## 12. REFERENCES

1. Java Documentation - Oracle
2. Java Swing Tutorial - Oracle
3. Object-Oriented Programming Concepts - Java Tutorials
4. Effective Java by Joshua Bloch
5. CSC241 Course Materials - COMSATS University
6. Design Patterns: Elements of Reusable Object-Oriented Software

---

**Report Prepared By:**  
Muzammil Ghaffar (Team Lead)  
Muhammad Zaeem  
Sadaqat Hussain  
Ahsan Raza  

**Submitted To:**  
Dr. Rizwan Rashid  
Department of Computer Science  
COMSATS University, Islamabad  

**Date:** December 17, 2025
