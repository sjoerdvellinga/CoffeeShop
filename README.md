# API Reference

## Getting Started
Application runs only on localhost, port 5000 (backend)  
Base URL: *http://127.0.0.1:5000/*

## Error Handling
Errors are returned as JSON objects:

**Example**:  
$ curl http://127.0.0.1:5000/NotValid  
  
{
  "error": 404,  
  "message": "resource not found",  
  "success": false  
}  
  
Other returned error codes:
404: Resource not found  
422: Unprocessable 

## Project dependencies
Setup a virtual envirionment with Python 3.9.

And install dependent packages from requirements.txt with command:

PIP3 install -r requirements.txt 

**Note**: Make sure that you are running version 1.0.1 of 'Werkzeug' or later. Earlier versions are not compatible with Python 3.9x.

### Project Server
From within the backend directory first ensure you are working using your created virtual environment.

To run the server, execute:

export FLASK_APP=flaskr
export FLASK_ENV=development
flask run

## Endpoints

### /drinks    (method: GET)
**General**:
Returns all the drinks on the menu

**Example**:
$ curl http://127.0.0.1:5000/drinks 
  
{  

  "drinks": [
    {
      "id": 1,
      "recipe": [
        {
          "color": "white",
          "parts": "1"
        },
        {
          "color": "green",
          "parts": "1"
        },
        {
          "color": "red",
          "parts": "1"
        }
      ],
      "title": "Vampire"
    }
  ],
  "success": true
}

### /drinks-details   (method: GET)
**General**:
*Returns the recipes for all drinks on the menu*

**Example**:
$ curl http://127.0.0.1:5000/drinks-details
{
  "drinks": [
    {
      "id": 1,
      "recipe": [
        {
          "color": "white",
          "name": "Tequila",
          "parts": "1"
        },
        {
          "color": "green",
          "name": "Lime juice",
          "parts": "1"
        },
        {
          "color": "red",
          "name": "Sangrita",
          "parts": "1"
        }
      ],
      "title": "Vampire"
    }
  ],
  "success": true
}

### /drinks   (method: POST)
**General**:
*Returns the recipes for all drinks on the menu*

**Example**:
curl http://127.0.0.1/5000/drinks -X POST -H "Content-type: application/json" -d '{
	"title":"Vampire",
	"recipe": [{"color": "white", "name":"Tequila", "parts":"1"},
				{"color": "green", "name":"Lime juice", "parts":"1"},
				{"color": "red", "name":"Sangrita", "parts":"1"}
	]
}'

### /drinks/<drink_id>   (method: DELETE)
**General**:
*Remove (delete) a menu item*

**Example**:
http://127.0.0.1/5000/drinks/1 -X DELETE

Get /drinks-details
General: This endpoint will return a detailed information from drinks.

Sample: curl http://127.0.0.1:5000/categories

### /drinks/<drink_id>   (method: PATCH)
**General**:
*Update name or recipe of selected drink*

**Example**:
curl http://127.0.0.1/5000/drinks -X PATCH -H "Content-type: application/json" -d '{
	"title":"Margarita"
}'