# assignment_designing_nosql_data_models
I'll have one data model hold the SQL please

Synopsis
-----
Below is my NoSQL data model design for the following basic, intermediate and advanced scenarios.

Basic
1. You're building an application that requires user login. Once logged in the user has a bunch of profile information and preference settings available to them. They will need to be able to set their birthday, gender, phone number and location (city, state, country). They should be able to provide text to tell about themselves. They also should be able to enable and disable the visibility of their birthday, gender, phone number, and location.

```
## users table
* username: string (must contain alpha, numbers or underscore only)
* password: string (must be at least 8 characters)
* aboutMe: string
* profile:
	* birthday: date (in this format: YYYY-MM-DD)
	* gender: string (M or F only)
	* phoneNumber: string (in this format: ###-###-####)
	* location: 
		* city: string
		* state: string
		* country: string
* profileVisibilityFlag: number (1 or 0 only)
```

Intermediate
1. You're building a restaurant table reserving app that allows users to reserve tables for specified numbers of people. The app will need to show only tables that are available and the times they are available. The app will need to store reservations under a given name with a phone number and number of guests.

```
## tablesAvailable table
* id: number
* availableTimes: [] of numbers
	* example: [12,14,17] means the table is available at 12pm-12:59pm, 2-2:59pm and 5-5:59pm

## reservations table
* name: string
* phoneNumber: string (in this format: ###-###-####)
* reservation_for: number
```

2. You're building a backend for a university that requires students to be able to login. Once logged in, the students can view the exam grades for their classes. They should be able to view results by semester. Each semester should only show the classes in which that student is enrolled that semester.

```
## grades table
* notes: each school year produces a new table for the student
	* example: school year Fall 2017, Spring 2018, Summer 2018 produces 1 table as follows: 

* studentId: number
* semester: 
	* fall: 
		* class (string): grade (string)
	* spring:
		* class (string): grade (string)
	* summer:
		* class (string): grade (string)
```

Advanced
1. Your eCommerce business needs to keep track of products and their prices. The products each belong to a department. The business needs to keep track of revenue as product prices change over time. The business also needs to keep track of receipts of transactions and the number of units each product has in stock.

```
## products table
* productId: number
* productName: string
* departmentId: number
* departmentName: string
* price: number
* inStock: number

## productRevenue table
* productId: number
* date: date
* priceSold: number
* quantitySold: number
* revenue: number (calculated value based on priceSold and quantitySold)
```

2. You're building an activity feed for a social media site. The feed must display a chronological list of activities for the current user's friends. These activities could potentially be any action performed on the site including uploading a photo, changing their profile, friending another user, commenting, liking etc... Further, you only want to display activities for users that the current user interacts with frequently.

```
## activities table
* id: number
* activitiesLog: [] of {date (date): activity (string)}
* friends: [] of number (of ids)
```

#### by Dennis C :coffee:
