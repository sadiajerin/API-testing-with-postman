# API-testing-with-postman


This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API. 

### **Features**

- Tests for GET, POST, PUT, DELETE requests
- Collection of tests covering different API endpoints
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

## API Documentation:
- https://documenter.getpostman.com/view/34702675/2sAXjRVoxd
  
### **Technology used:**
- Postman
- Newman

### **Prerequisite:**
- Node Js
- Newman
- Newman Html Report Library

### **Installation**

1. Postman: If you haven't already, [download and install Postman.](https://www.postman.com/downloads/)
2. Clone the repository:
 ```console 
  git clone https://github.com/sadiajerin/API-testing-with-postman.git
```
3. Import the Postman collection:
    - Open Postman.
    - Click on the Import button.
    - Select the file from the repository.
4. Import the Postman environment:
    - In Postman, click on the gear icon in the top right corner.
    - Select **Import** and choose the file.
5. Newman and Report Installation Process:
    - Newman Install Command:
     ```console 
      npm install -g newman
    ```
    - Newman Html Report Install Command:
     ```console 
      npm install -g newman-reporter-htmlextra
    ```
### **Usage**
1. Select Environment:
    -   In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
3. Run Collection:
    -   Select the imported collection from the Collections sidebar.
    -   Click on the Runner button to open the collection runner.
    -   Select the desired environment.
    -   Click Start Test to run the collection.
8. View Results:
    -   Once the tests are complete, view the results in the Runner tab.
    -   Detailed test results can be viewed for each request.

## **Testing**

## Test Case Scenarios:

## _**1. Create New Booking**_

### Request URL: https://restful-booker.herokuapp.com/booking/
### Request Method: POST
### Pre-request Script:
```console 
    var firstName = pm.variables.replaceIn("{{$randomFirstName}}")
    pm.environment.set("firstName", firstName)
    console.log("First Name Value "+firstName)
    
    var lastName = pm.variables.replaceIn("{{$randomLastName}}")
    pm.environment.set("lastName", lastName)
    console.log("Last Name Value "+lastName)
    
    var totalPrice = pm.variables.replaceIn("{{$randomInt}}")
    pm.environment.set("totalPrice", totalPrice)
    console.log(totalPrice)
    
    var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}")
    pm.environment.set("depositPaid", depositPaid)
    console.log(depositPaid)
    
    //Date
    const moment = require('moment')
    const today = moment()
    pm.environment.set("checkin", today.add(1,'d').format("YYYY-MM-DD"))
    pm.environment.set("checkout",today.add(5,'d').format("YYYY-MM-DD") )
    
    var additionalNeeds = pm.variables.replaceIn("{{$randomNoun}}")
    pm.environment.set("additionalNeeds", additionalNeeds)
```
  **Request Body:** 
 ```console 
  {
	  "firstname" : "{{firstName}}",
	  "lastname" : "{{lastName}}",
	  "totalprice" : {{totalPrice}},
	  "depositpaid" : {{depositPaid}},
	  "bookingdates" : {
    	  "checkin" : "{{checkin}}",
    	  "checkout" : "{{checkout}}"
	  },
	  "additionalneeds" : "{{additionalNeeds}}"
  }
```
  **Response Body:**
 ```console 
  {
      "bookingid": 4334,
      "booking": {
          "firstname": "Joelle",
          "lastname": "Krajcik",
          "totalprice": 266,
          "depositpaid": true,
          "bookingdates": {
              "checkin": "2024-03-15",
              "checkout": "2024-03-20"
          },
          "additionalneeds": "monitor"
      }
  }
```
 ## _**2. Get Booking Details By ID**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: GET
### Response Body:
 ```console 
{
    "firstname": "D'angelo",
    "lastname": "Feeney",
    "totalprice": 757,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2024-03-15",
        "checkout": "2024-03-20"
    },
    "additionalneeds": "hard drive"
}
```
## _**3. Create A Token For Authentication.**_
### Request URL: https://restful-booker.herokuapp.com/auth
### Request Method: POST
### Pre-request Script: None
### Request Body:
 ```console 
{
	"username": "admin",
	"password": "password123"
}
```
  **Response Body:**
 ```console 
{
    "token": "06eb798bf6f2caa"
}
```

 ## _**4. Update the Booking Details**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: PUT
### Pre-request Script:
```console 
    var firstName = pm.variables.replaceIn("{{$randomFirstName}}")
    pm.environment.set("firstName", firstName)
    console.log("First Name Value "+firstName)
    
    var lastName = pm.variables.replaceIn("{{$randomLastName}}")
    pm.environment.set("lastName", lastName)
    console.log("Last Name Value "+lastName)
    
    var totalPrice = pm.variables.replaceIn("{{$randomInt}}")
    pm.environment.set("totalPrice", totalPrice)
    console.log(totalPrice)
    
    var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}")
    pm.environment.set("depositPaid", depositPaid)
    console.log(depositPaid)
    
    //Date
    const moment = require('moment')
    const today = moment()
    pm.environment.set("checkin", today.add(1,'d').format("YYYY-MM-DD"))
    pm.environment.set("checkout",today.add(5,'d').format("YYYY-MM-DD") )
    
    var additionalNeeds = pm.variables.replaceIn("{{$randomNoun}}")
    pm.environment.set("additionalNeeds", additionalNeeds)
```
  **Request Body:** 
 ```console 
  {
	  "firstname" : "{{firstName}}",
	  "lastname" : "{{lastName}}",
	  "totalprice" : {{totalPrice}},
	  "depositpaid" : {{depositPaid}},
	  "bookingdates" : {
    	  "checkin" : "{{checkin}}",
    	  "checkout" : "{{checkout}}"
	  },
	  "additionalneeds" : "{{additionalNeeds}}"
  }
```
  **Response Body:**
 ```console 
  {
      "bookingid": 4334,
      "booking": {
          "firstname": "Joelle",
          "lastname": "Krajcik",
          "totalprice": 266,
          "depositpaid": true,
          "bookingdates": {
              "checkin": "2024-03-15",
              "checkout": "2024-03-20"
          },
          "additionalneeds": "monitor"
      }
  }
```

 ## _**5. Delete Booking Record**_

### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: DELETE
### Response Body: None 

## Run Command:  
- Run Command for Console: 
```console 
newman run batch25.postman_collection.json -e batch25.postman_environment.json 
```
- Run Command for Report: 
```console 
newman run batch25.postman_collection.json -e batch25.postman_environment.json -r cli,htmlextra 
```

## Newman Report Summary:
![image](https://github.com/user-attachments/assets/a8b10b2c-2ad0-4869-80ab-4b61f3ad3a77)

![image](https://github.com/user-attachments/assets/a550990a-0b8c-4cde-b6e5-a3f685beea4d)

![image](https://github.com/user-attachments/assets/def624d2-2d8a-441d-b278-75447ebb33cb)

![image](https://github.com/user-attachments/assets/c714f54c-428f-49f2-8d4e-c581c593c627)
![image](https://github.com/user-attachments/assets/02f86f81-e6f7-4c88-b593-73d844012330)
![image](https://github.com/user-attachments/assets/150832bd-3e67-4b31-bc83-a3c127fc6051)



    
