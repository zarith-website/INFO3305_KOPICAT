# STUDENT ATTENDANCE MANAGEMENT SYSTEM (SAMS)

**Course:** INFO 3305 Web Application Development  
**Semester:** 1, 2025/2026 — Section 4  
**Submission deadline:** 12/12/2025

## Group Members
- Ahmad Faiz Bin Abdul Karim (2316083)
- Puteri Areefa Aura Binti Kamaruzzaman (2319958)
- Zarith Sofea Binti Hazzarul Hisham (2315270)
- Nor Syazana Binti Mohd Ansar (2319258)
- Nur Maisarah Binti Roslan (2311284)

## Lecturer
Dr. Najhan bin Muhamad Ibrahim

---

# 📑 Part A: Proposal

## 1. Introduction
The Student Attendance Management System (SAMS) is a web-based application designed to simplify and digitize the process of recording and managing student attendance in educational institutions. Traditionally, attendance is marked manually on paper, whichW can lead to inefficiency, data loss and errors. SAMS, developed using the Laravel Framework, utilizes the Model-View-Controller (MVC) architecture to ensure a structured and scalable system.
Laravel’s technologies such as Eloquent ORM, Blade Template Engine, and Artisan CLI are used to manage data, build responsive user interfaces, and automate backend tasks. This application allows administrators and teachers to manage student records, classes, and attendance efficiently through a user-friendly dashboard accessible from any device.

## 2. Problem Description
In many educational institutions, instructors still rely on manual methods such as paper registers or spreadsheets to record attendance. This process is time-consuming, prone to mistakes, and difficult to maintain over time. It also affects the institution’s ability to monitor student participation, which may influence academic performance (Zuanuwar, 2020). The proposed application will be a web-based system accessible through any browser, allowing instructors and administrators to manage attendance more effectively and securely.

The current attendance system faces several challenges. This is because manual attendance tracking is inefficient and error-prone. There is no centralized system for storing attendance records, making reports and analysis difficult. Additionally, the existing methods are not scalable or easily accessible. These challenges highlight the need for modern, automated solutions.

## 3. Objectives
- To automate the attendance recording process, reducing manual errors.
- To store and manage student information systematically using a relational database.
- To allow teachers and administrators to view, update, and generate attendance reports easily.
- To provide real-time insights into student attendance rates for performance analysis.
- To implement Laravel’s MVC structure for better separation of logic, scalability, and maintainability.

## 4. Project Scope
The Student Attendance Management System (SAMS) aims to make the attendance process faster, easier, and more reliable by replacing manual methods with a digital system. The system allows lecturers to take attendance, view student records, and generate reports through an online platform. Administrators can manage users, classes, and attendance data in one place.

The main features include:
- Secure login for admin and lecturers.
- Managing student and class information.
- Recording and editing attendance.
- Generating attendance reports.
- A simple, user-friendly dashboard that works on multiple devices.

Targeted User
SAMS is designed mainly for:
1. Administrators – to manage user accounts, student details, and reports.
2. Lecturers – to take attendance, update records, and monitor attendance trends.
3. Students – in the future, they may be able to view their own attendance records.

Specific Platform
The system will be a web-based application built using the Laravel Framework with a MySQL database. It can run on any browser such as Chrome, 				Firefox, or Edge, and will use HTML, CSS, Blade, and JavaScript for the interface. The system can be hosted locally or on a cloud platform.


## 5 Constraints
The SAMS project has a few limitations that may affect its development and testing:
- Time: The project must be finished within the semester, so there is limited time for testing, adding new features, or improving the design.
- Resources: Development relies on student laptops and free tools. This limits how much data can be stored or processed.
- Budget: There is little to no funding for this project, so free hosting and open-source tools are used instead of paid ones.
- Testing: Real users like lecturers or administrators might not always be available for testing, so the team may have to use demo data.
- Skills: Not all team members are experts in Laravel or web development, so some parts may take longer to complete.
- Internet: Since it’s web-based, the system needs a stable internet connection. Poor connectivity can affect system performance.
- Security: The system stores student data, so extra care is needed to prevent unauthorized access or data loss.
- Maintenance: After deployment, the system may need updates or bug fixes, but ongoing maintenance could be limited due to time and resource constraints.

## 6 Project Stages
The development of SAMS follows the System Development Life Cycle (SDLC) to ensure a structured and organized workflow. The project is divided into the following five stages:

**Phase 1: Requirement Analysis & Planning**
- Identifying the core problems with the current manual attendance system.
- Gathering requirements from potential users (lecturers and admins).
- Defining the project objectives, scope, and feasibility.
**Phase 2: System Design**
- Designing the system architecture based on the MVC (Model-View-Controller) pattern.
- Creating the Entity Relationship Diagram (ERD) to structure the database.
- Designing the User Interface (UI) mockups and the Sequence Diagrams to visualize user interactions.
**Phase 3: Implementation (Development)**
1. Setting up the Environment
- Installing Laravel and connecting it to the database so the project is ready to start.
2. Backend Development
- Creating the database tables (using migrations) to store student and attendance info, and writing the code (controllers) to handle the logic, like saving or deleting records.
3. Frontend Development
- Designing the website pages (like the login screen and dashboard) using Laravel Blade, HTML, and CSS so it looks good and is easy to use.
4. Integration
- Connecting the design (Frontend) with the logic (Backend) to make sure the buttons and forms work correctly.
**Phase 4: Testing**
- Unit Testing: Checking individual components (e.g., ensuring a student cannot be added twice).
- User Acceptance Testing (UAT): Verifying that the flow from login to marking attendance works smoothly and meets the objectives defined in Phase 1.
- Debugging errors and optimizing code performance.
**Phase 5: Documentation & Deployment**
- Compiling the final project report, including system documentation and user manuals.
- Preparing the presentation slides for the project defense.
- Final submission of the source code and documentation.

## 5. Database Design (ERD)

```mermaid
erDiagram
    Classrooms {
        int id PK
        string name
        int teacher_id
        datetime updated_at
        datetime created_at
    }

    Students {
        int id PK
        string name
        int student_id
        int classroom_id FK
        datetime created_at
    }

    Attendances {
        int id PK
        date date
        string status
        int student_id FK
        datetime created_at
    }

    Classrooms ||--o{ Students : "has"
    Students ||--o{ Attendances : "records"
```

## 6. Sequence Diagram

```mermaid
sequenceDiagram
    autonumber

    participant T as Teacher (User)
    participant V as Web Browser (View)
    participant C as Laravel Controller
    participant M as Model (Eloquent/DB)

    T ->> V: Open "Mark Attendance" Page
    V ->> C: GET /attendance/create
    C ->> M: Retrieve class and student list
    M -->> C: Return data
    C -->> V: Render attendance form (Blade View)
    V -->> T: Display Attendance Form

    T ->> V: Submit attendance data
    V ->> C: POST /attendance/store
    C ->> M: Save attendance record
    M -->> C: Confirm success
    C -->> V: Redirect to attendance list view
    V -->> T: Display "Attendance Recorded Successfully"
```
# 📑 Part B: Final Report

## 7. Implementation
The system was implemented using **Laravel 10**, **PHP 8**, **MySQL**, and **Bootstrap**.  

- **Environment Setup:** Installed Laravel framework, configured `.env` file, and connected to MySQL database.  
- **Database Migrations:** Created tables for `students`, `classrooms`, and `attendances` using Laravel migrations.  
- **Models & Controllers:** Developed Eloquent models and controllers to handle CRUD operations for students, classes, and attendance.  
- **Routes:** Defined web routes for login, student management, class management, and attendance marking.  
- **Frontend (Blade Templates):** Designed user interface pages (login, dashboard, attendance form, reports) using Blade, HTML, CSS, and Bootstrap.  
- **Integration:** Connected frontend forms with backend logic to ensure smooth data flow and validation.  

### Example Code Snippet
```php
// AttendanceController@store
public function store(Request $request) {
    $validated = $request->validate([
        'classroom_id' => 'required|exists:classrooms,id',
        'records' => 'required|array',
    ]);
    foreach ($request->records as $record) {
        Attendance::create([
            'student_id' => $record['student_id'],
            'classroom_id' => $request->classroom_id,
            'date' => now(),
            'status' => $record['status'],
        ]);
    }
}


```
## 8. Testing

Testing was conducted in two phases:

### 🔹 Unit Testing
- Verified CRUD operations for students, classes, and attendance records.  
- Ensured validation rules worked correctly (e.g., preventing duplicate student entries).  
- Checked database integrity after migrations and updates.  

### 🔹 User Acceptance Testing (UAT)
- Simulated the full workflow: login → mark attendance → generate report.  
- Confirmed that lecturers and administrators could navigate the system smoothly.  
- Validated that attendance records were stored and displayed correctly.  

### 🔹 Bug Fixes
- Addressed issues such as incorrect data rendering in reports.  
- Fixed validation errors in forms (e.g., empty fields, duplicate entries).  
- Improved UI alignment and responsiveness across devices.  

### 📸 Screenshots
*(Insert screenshots of test results or console outputs here)*  
- Example: Validation error when adding duplicate student.  
- Example: Successful attendance submission message.  
- Example: Generated attendance report output.  

## 9. Results & Screenshots

The final system is fully functional and meets the objectives outlined in the proposal.  

### 📸 Login Page
![Login Page](assets/login.png)  

### 📸 Dashboard
![Dashboard](assets/dashboard.png)  

### 📸 Attendance Form
![Attendance Form](assets/attendance.png)  

### 📸 Reports Page
![Reports Page](assets/reports.png)  

The system successfully automates attendance tracking, centralizes data, and provides analytics.  
Challenges such as time constraints and limited Laravel experience were overcome through teamwork and iterative testing.  

## 10. Constraints

- Limited time within the semester restricted feature expansion.  
- Restricted resources (student laptops, free hosting).  
- Budget limitations requiring open-source tools.  
- Varying levels of Laravel expertise among team members.  
- Need for stable internet connectivity for testing and deployment.  
- Security concerns in handling student data required careful validation and access control.

## 11. Significance of the Project

SAMS provides a practical solution to a common problem in education.  

- **Lecturers:** Reduced paperwork and faster attendance marking.  
- **Administrators:** Centralized access to data and reporting tools.  
- **Institutions:** Improved accuracy, scalability, and performance tracking.  

The project also allowed our group to apply Laravel concepts in a real-world context, enhancing both technical and teamwork skills. 

## 12. Conclusion

SAMS is a Laravel-based web application that digitizes attendance management.  
It replaces manual methods with a secure, scalable, and user-friendly system.  

The project demonstrates our ability to design, implement, and test a complete MVC web application.  
It also highlights the importance of teamwork, problem-solving, and applying theoretical knowledge in a practical context.  

### 🔮 Future Improvements
- Student self-check attendance.  
- Mobile app integration for easier access.  
- Advanced analytics and reporting features.  
- Role-based access control for enhanced security.  

## 13. References
- Zuanuwar, S. H. (2020). *The Influence Student Attendance Management System on Academic Performance*. Journal of Social Transformation and Education.

## 14. Mock-up
- https://github.com/zarith-website/INFO3305_KOPICAT/blob/main/Mockup%20Log%20In.jpeg?raw=true
- https://github.com/zarith-website/INFO3305_KOPICAT/blob/main/Mockup%20Dashboard.jpeg?raw=true

---

# STUDENT ATTENDANCE MANAGEMENT SYSTEM (SAMS)

**Course:** INFO 3305 Web Application Development  
**Semester:** 1, 2025/2026 — Section 4  
**Submission deadline:** 12/12/2025

## Group Members
- Ahmad Faiz Bin Abdul Karim (2316083)
- Puteri Areefa Aura Binti Kamaruzzaman (2319958)
- Zarith Sofea Binti Hazzarul Hisham (2315270)
- Nor Syazana Binti Mohd Ansar (2319258)
- Nur Maisarah Binti Roslan (2311284)

## Lecturer
Dr. Najhan bin Muhamad Ibrahim

---

# 📑 Part B: Final Report

## 1. Introduction
The Student Attendance Management System (SAMS) is a web-based application designed to simplify and digitize the process of recording and managing student attendance in educational institutions. Traditionally, attendance is marked manually on paper, whichW can lead to inefficiency, data loss and errors. SAMS, developed using the Laravel Framework, utilizes the Model-View-Controller (MVC) architecture to ensure a structured and scalable system.
Laravel’s technologies such as Eloquent ORM, Blade Template Engine, and Artisan CLI are used to manage data, build responsive user interfaces, and automate backend tasks. This application allows administrators and teachers to manage student records, classes, and attendance efficiently through a user-friendly dashboard accessible from any device.

## 2. Problem Description
In many educational institutions, instructors still rely on manual methods such as paper registers or spreadsheets to record attendance. This process is time-consuming, prone to mistakes, and difficult to maintain over time. It also affects the institution’s ability to monitor student participation, which may influence academic performance (Zuanuwar, 2020). The proposed application will be a web-based system accessible through any browser, allowing instructors and administrators to manage attendance more effectively and securely.

The current attendance system faces several challenges. This is because manual attendance tracking is inefficient and error-prone. There is no centralized system for storing attendance records, making reports and analysis difficult. Additionally, the existing methods are not scalable or easily accessible. These challenges highlight the need for modern, automated solutions.

## 3. Objectives
- To automate the attendance recording process, reducing manual errors.
- To store and manage student information systematically using a relational database.
- To allow teachers and administrators to view, update, and generate attendance reports easily.
- To provide real-time insights into student attendance rates for performance analysis.
- To implement Laravel’s MVC structure for better separation of logic, scalability, and maintainability.

## 4. Features and Description

| **Feature**              | **Description**                                                                 |
|---------------------------|---------------------------------------------------------------------------------|
| User Authentication       | Secure login for admin and teachers using Laravel Breeze or Jetstream.         |
| Student Management (CRUD) | Add, view, edit, and delete student records.                                   |
| Class Management          | Create and manage class lists and assign students.                             |
| Attendance Management (CRUD) | Mark daily attendance, edit or delete records, and view history.           |
| Reports and Analytics     | Generate attendance reports by date, class, or student.                        |
| Dashboard Overview        | View summary of total students, classes, and attendance percentage.            |


## 5. Database Design (ERD)

```mermaid
erDiagram
    Classrooms {
        int id PK
        string name
        int teacher_id
        datetime updated_at
        datetime created_at
    }

    Students {
        int id PK
        string name
        int student_id
        int classroom_id FK
        datetime created_at
    }

    Attendances {
        int id PK
        date date
        string status
        int student_id FK
        datetime created_at
    }

    Classrooms ||--o{ Students : "has"
    Students ||--o{ Attendances : "records"
```

## 6. Sequence Diagram

```mermaid
sequenceDiagram
    autonumber

    participant T as Teacher (User)
    participant V as Web Browser (View)
    participant C as Laravel Controller
    participant M as Model (Eloquent/DB)

    T ->> V: Open "Mark Attendance" Page
    V ->> C: GET /attendance/create
    C ->> M: Retrieve class and student list
    M -->> C: Return data
    C -->> V: Render attendance form (Blade View)
    V -->> T: Display Attendance Form

    T ->> V: Submit attendance data
    V ->> C: POST /attendance/store
    C ->> M: Save attendance record
    M -->> C: Confirm success
    C -->> V: Redirect to attendance list view
    V -->> T: Display "Attendance Recorded Successfully"
```
# 📑 Part B: Final Report

## 7. Implementation
The system was implemented using **Laravel 10**, **PHP 8**, **MySQL**, and **Bootstrap**.  

- **Environment Setup:** Installed Laravel framework, configured `.env` file, and connected to MySQL database.  
- **Database Migrations:** Created tables for `students`, `classrooms`, and `attendances` using Laravel migrations.  
- **Models & Controllers:** Developed Eloquent models and controllers to handle CRUD operations for students, classes, and attendance.  
- **Routes:** Defined web routes for login, student management, class management, and attendance marking.  
- **Frontend (Blade Templates):** Designed user interface pages (login, dashboard, attendance form, reports) using Blade, HTML, CSS, and Bootstrap.  
- **Integration:** Connected frontend forms with backend logic to ensure smooth data flow and validation.  

### Example Code Snippet
```php
// AttendanceController@store
public function store(Request $request) {
    $validated = $request->validate([
        'classroom_id' => 'required|exists:classrooms,id',
        'records' => 'required|array',
    ]);
    foreach ($request->records as $record) {
        Attendance::create([
            'student_id' => $record['student_id'],
            'classroom_id' => $request->classroom_id,
            'date' => now(),
            'status' => $record['status'],
        ]);
    }
}


```
## 8. Testing

Testing was conducted in two phases:

### 🔹 Unit Testing
- Verified CRUD operations for students, classes, and attendance records.  
- Ensured validation rules worked correctly (e.g., preventing duplicate student entries).  
- Checked database integrity after migrations and updates.  

### 🔹 User Acceptance Testing (UAT)
- Simulated the full workflow: login → mark attendance → generate report.  
- Confirmed that lecturers and administrators could navigate the system smoothly.  
- Validated that attendance records were stored and displayed correctly.  

### 🔹 Bug Fixes
- Addressed issues such as incorrect data rendering in reports.  
- Fixed validation errors in forms (e.g., empty fields, duplicate entries).  
- Improved UI alignment and responsiveness across devices.  

### 📸 Screenshots
*(Insert screenshots of test results or console outputs here)*  
- Example: Validation error when adding duplicate student.  
- Example: Successful attendance submission message.  
- Example: Generated attendance report output.  

## 9. Results & Screenshots

The final system is fully functional and meets the objectives outlined in the proposal.  

### 📸 Login Page
![Login Page](assets/login.png)  

### 📸 Dashboard
![Dashboard](assets/dashboard.png)  

### 📸 Attendance Form
![Attendance Form](assets/attendance.png)  

### 📸 Reports Page
![Reports Page](assets/reports.png)  

The system successfully automates attendance tracking, centralizes data, and provides analytics.  
Challenges such as time constraints and limited Laravel experience were overcome through teamwork and iterative testing.  

## 10. Constraints

- Limited time within the semester restricted feature expansion.  
- Restricted resources (student laptops, free hosting).  
- Budget limitations requiring open-source tools.  
- Varying levels of Laravel expertise among team members.  
- Need for stable internet connectivity for testing and deployment.  
- Security concerns in handling student data required careful validation and access control.

## 11. Significance of the Project

SAMS provides a practical solution to a common problem in education.  

- **Lecturers:** Reduced paperwork and faster attendance marking.  
- **Administrators:** Centralized access to data and reporting tools.  
- **Institutions:** Improved accuracy, scalability, and performance tracking.  

The project also allowed our group to apply Laravel concepts in a real-world context, enhancing both technical and teamwork skills. 

## 12. Conclusion

SAMS is a Laravel-based web application that digitizes attendance management.  
It replaces manual methods with a secure, scalable, and user-friendly system.  

The project demonstrates our ability to design, implement, and test a complete MVC web application.  
It also highlights the importance of teamwork, problem-solving, and applying theoretical knowledge in a practical context.  

### 🔮 Future Improvements
- Student self-check attendance.  
- Mobile app integration for easier access.  
- Advanced analytics and reporting features.  
- Role-based access control for enhanced security.  

## 13. References
- Zuanuwar, S. H. (2020). *The Influence Student Attendance Management System on Academic Performance*. Journal of Social Transformation and Education.

## 14. Mock-up
- https://github.com/zarith-website/INFO3305_KOPICAT/blob/main/Mockup%20Log%20In.jpeg?raw=true
- https://github.com/zarith-website/INFO3305_KOPICAT/blob/main/Mockup%20Dashboard.jpeg?raw=true

---
