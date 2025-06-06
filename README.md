# Event_Planner
Event Planner is a web application for creating, managing, and RSVPing to events. It supports user authentication with admin and user roles, allowing admins to create and edit events while users can view and RSVP to them. The application is built with Spring Boot, MySQL, Thymeleaf, and Spring Security, providing a secure and scalable event management solution.

# Table of Contents
Project Setup and Installation
Technologies Used
ER Diagram
API Endpoints

# Project Setup and Installation

Java 17: Required for Spring Boot 3.5.0.
Maven 3.6+: For dependency management and building the project.
MySQL 8.0+: Database for storing users, events, and RSVPs.
Git: For cloning the repository.
IDE: Recommended (e.g., IntelliJ IDEA, Eclipse, or VS Code).

# Installation Steps
1. Clone the Repository:
   git clone https://github.com/sanjee-jha/Event_Planner.git
   cd Event_Planner
   
2. Set Up MySQL: CREATE DATABASE event_planner; 

3. src/main/resources/application.properties
   spring.datasource.username=root
   spring.datasource.password=root

4. Build the Project:    mvn clean install -> mvn spring-boot:run

5. Register an Admin User:
   Open http://localhost:8080/register.
   Create an admin account (e.g., username: admin, password: admin123, role: Admin).
   Log in at http://localhost:8080/login.

6. Test the Application:
    As an admin, create an event at http://localhost:8080/events (click "Create New Event").
    As a user, RSVP to events on the same page.

 # Technologies Used
    Spring Boot 3.5.0:
      Why: Simplifies Java web development with auto-configuration, embedded Tomcat, and a            robust ecosystem. Ideal for rapid development of RESTful and MVC applications.

    MySQL 8.0+:
      Why: A reliable, widely-used relational database for persistent storage of users, events,       and RSVPs. Supports complex queries and transactions.

   Spring Data JPA:
     Why: Abstracts database operations with a repository pattern, reducing boilerplate code for      CRUD operations.

   Thymeleaf:
     Why: Server-side templating engine for rendering dynamic HTML views. Integrates seamlessly       with Spring Boot for secure, role-based UI rendering.
   
  Spring Security:
     Why: Provides robust authentication and authorization, enabling role-based access (admin         vs. user) and secure password hashing.
  
  Maven:
     Why: Manages dependencies and builds, ensuring consistent project setup across environments.

 Lombok:
   Why: Reduces boilerplate code for Java models (e.g., getters, setters) to improve readability    and maintainability.

# ER Diagram

Below is a text-based representation of the Entity-Relationship Diagram for the Event Planner database:

+-------+       +-------+       +-------+
| User  |       | Event |       | RSVP  |
+-------+       +-------+       +-------+
| id    |<----->| id    |<----->| id    |
| username |    | title |       | user_id |
| password |    | description | | event_id|
| role  |       | start_time |  | status |
+-------+       | end_time |    +-------+
                | location |
                +-------+

Relationships:
- User 1:N RSVP (One user can RSVP to many events)
- Event 1:N RSVP (One event can have many RSVPs)
- RSVP M:1 User (Many RSVPs belong to one user)
- RSVP M:1 Event (Many RSVPs belong to one event)


# Entities:
User: Stores user details (ID, username, password, role: ADMIN or USER).
Event: Stores event details (ID, title, description, start_time, end_time, location).
RSVP: Links users to events with a status (e.g., GOING, NOT_GOING).


# API Endpoints
The application uses Thymeleaf for server-side rendering, but the following endpoints handle HTTP requests for key functionalities. All endpoints are prefixed with http://localhost:8080.




# HTTP Method                Route                                  Purpose

| GET         | `/register`                        | Displays the user registration form.         
| POST        | `/register`                        | Registers a new user (admin or user role).   |
| GET         | `/login`                           | Displays the login form.                     |
| POST        | `/login`                           | Authenticates a user.                        |
| GET         | `/events`                          | Lists all events (users can RSVP, admins can manage). |
| GET         | `/events/admin/event`              | Displays the event creation form (admin 
|
| POST        | `/events/admin/event`              | Creates a new event (admin only).            |
| GET         | `/events/admin/event/edit/{id}`    | Displays the event edit form (admin only).   |
| POST        | `/events/admin/event/edit/{id}`    | Updates an existing event (admin only).      |
| POST        | `/events/{id}/rsvp`                | Submits an RSVP for an event (users only).   |



# Deployed Application
   Not deployed yet
   
