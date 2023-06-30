# The International FemHack II

## Backend Challenge
Welcome participants to **The International FemHack edition II Backend challenge**.

This documents shows  a *possible* implementation of the endpoints presented on `Task 3` and clarifies concepts explained on the NUWE's Landing page.

> :warning: **Attention!** This document is ONLY a possible implementation. The implementation can be DIFFERENT as the evaluation does not entirely evualate achieving the objective but also score the decision making written down on the README.md provided. :warning:

## Task 1 and Task 2

- The access control authentication can be implemented using, for example **JWT**.
- The role system is up to the participants, we **recommend** to have at least 2 roles, `user` and `admin`.
- Encryption algorithm should be discussed on the documentation provided and the reasons must be clear.
- How the passwords, users and roles are stored is UP to the participants but either if it is a filesystem database, an SQL database, a Graph database or whatever, it **SHOULD** be clarified in the documentation why and how has been implemented.

## Task 3: Authenticated endpoints

Task 3 is about implementing endpoints to check the authentication of registered and unregistered users as well as developing a logging system (to create logs).

This task can be divided into 2 section:

### Section 1: Role checking

The proposed endpoint is `/home`.

This endpoints does the following
- If the **user** is registered it returns a message with the **Username** and the **Role** of the user.
- If the **user** is NOT registered it returns a message saying something along the lines of not being registered.

Example:
```jsonc
// Example /home registered as Hector with role User
{
    "message": "Welcome back Hector! Your current role is User. Great to have you back."
}

// Example /home not registered
{
    "message": "Welcome to the /home page. You are not registered on the website."
}
```

### Section 2: Logging system

The proposed endpoint is `/log` which should be restricted to users with the maximum permission role (`Administrator`). 
This endpoints allows administrators to extract connection that have been made to the website. 
The endpoint should:
1) Extract latest 25 connections made to the server.
2) Extract all the connections. Not at once, but the possibily for example to extract all the connections must be available.
3) Connections are literally **HTTP** calls. It should store *at least* the following:
    1) **IP** of the client.
    2) Formatted **date** representing when the connection has been made.
    3) HTTP verb used (such as **GET**, **POST**, **PUT**, etc).
    4) To which endpoint the connection points to.

Example of logging connection:
```json
{
    "ip" : "146.237.236.10",
    "date" : "Sep 20, 2023",
    "http-verb": "GET",
    "endpoint": "/home"
}
```

---
> Created by NUWE with :heart:
