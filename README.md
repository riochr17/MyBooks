# MyBooks Project

Most loved booking Gateway, only 3 steps to finish your booking problem 

## Table of Contents
- [ Instalation ](#instalation)
- [ Usage ](#usage)
	- [ A. Register/Login ](#a)
	- [ B. Start an Order ](#b)
		- [ B.1. Create Order ID ](#b1)
		- [ B.2. Fill the Form ](#b2)
	- [ C. Check Order Status ](#c)
- [ History ](#history)
- [ Credits ](#credits)

<a name="instalation"></a>
## Installation

No installation required

<a name="usage"></a>
## Usage

1. Register / Login to get JWT Token
2. Start an order for user
3. Check Order Status

<a name="a"></a>
### A. Register/Login

request
```
POST /api/v1/login
Content-Type: application/json
Authorization: Bearer eyJh...
{
	"username": "testing",	// required
	"password": "123asd"	// required
}
```

response
```
{
    "email": "riochr17@gmail.com",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NDMzMjE4NjgsInVzZXJpZCI6IjA4NjFjZGE5LTVhNTEtNDc4Ni04NGMwLTE3NTlkMzNjZDkwNSJ9.JpcRdaljs3g9AcYWv73zSyl3E_vfjrTVaUr0azvEl34",
    "username": "rio"
}
```

<a name="b"></a>
### B. Start an Order

<a name="b1"></a>
#### B.1. Create Order ID

request
```
POST /api/v1/order
Content-Type: application/json
Authorization: Bearer eyJh...
{
	"items": [
		{
			"name": "Buku",	// required
			"price": 5000,	// required
			"quantity": 1	// required
		},...
	],
	"forms": [
		{
			"key": "NoHP",		// required
			"hint": "Nomor HP"	// required
		},...
	]
}
```

response
```
{
    "id": "93966728-1c6e-4fd0-be54-3e20e5d77fdc", <-- order id
    ...
    "total_price": 17000,
    "items": [
        {
            "id": "8a58e93d-e1b7-4ff9-a443-3837374fe0e6", <-- item id
            ...
            "updated_at": "2018-10-28T19:45:38.60346+07:00"
        },...
    ]
}
```

`93966728-1c6e-4fd0-be54-3e20e5d77fdc` is the order ID

<a name="b2"></a>
#### B.2. Fill the Form
Let user fill the order form by `GET /order/{order_id}` on browser, e.g. `GET /order/93966728-1c6e-4fd0-be54-3e20e5d77fdc`
On this step, no authorization required.

example form
![](image1.png "")

<a name="c"></a>
### C. Check Order Status

request
```
GET /api/v1/order
Authorization: Bearer eyJh...
```

response
```
[
    {
        "id": "f94ffb20-0d21-4ea7-968a-092374c78c56",
        ...
        "items": [
            {
                "id": "83c51bf8-cdba-4c70-b421-5cd4b5c5ea56",
                ...
                "updated_at": "2018-10-28T10:36:36Z"
            },...
        ]
    }
]
```

<a name="history"></a>
## History

1. 28/10/2018: Initialization

<a name="credits"></a>
## Credits

Rio