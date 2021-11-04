# virtual_care_lifepack_api
# Changelogs

## 2021-05-06
- Add new subscription status (`order_expired`) that will be triggered if user doesn't take any action with the unpaid order with incomplete address within 1 hour.
- Add new `expired_at` response parameter in [GET Subscription History](https://api-docs.lifepack.id/#0bb084e6-2e38-4c52-86c9-1a3f28e65553) endpoint.
- Add new `expired_at` response parameter in [GET Subscription Detail](https://api-docs.lifepack.id/#16595cf9-dfe3-4b83-a319-5e61d12464f9) endpoint.

## 2021-04-01
- Add new way to submit prescription data, using free text (`medications` parameter) in [POST Submit Prescription Data](https://api-docs.lifepack.id/#01382ce2-fb36-45cd-9077-a31495d47413) endpoint.

## 2021-02-22
- **[Breaking Changes]** Set parameter `city_id` to mandatory on request body parameter of [POST Submit Prescription Data](https://api-docs.lifepack.id/#01382ce2-fb36-45cd-9077-a31495d47413) endpoint.
- **[Breaking Changes]** Add required parameter `city_id` on request query parameter of [GET Product List](https://api-docs.lifepack.id/#ce261a0f-27ae-45dc-a6b2-a57f060a0343) endpoint.
- Updated the [GET City Coverage](https://api-docs.lifepack.id/#3dc6feaa-ac70-4738-ad87-2b6aa008229f) endpoint response values. We now support broader selection of cities to provide the best coverage and price offered possible to our partners.

## 2021-01-14
- **[Breaking Changes]** Add mandatory `dosage_per_unit` on product entity if you are using submit by digital prescription method on [POST Submit Prescription Data](https://api-docs.lifepack.id/#01382ce2-fb36-45cd-9077-a31495d47413) endpoint.
- Added optional `age_unit` in patient entity on [POST Submit Prescription Data](https://api-docs.lifepack.id/#01382ce2-fb36-45cd-9077-a31495d47413) endpoint. Default value is `years`.
- Added optional [`age`, `age_unit`, `weight`] in patient entity of request parameters on [POST Register Patient](https://api-docs.lifepack.id/#88f25b11-49ad-4272-a784-92893453b8ae) endpoint.

## 2020-12-21
- Change `diagnose` on patient entity max character length from 100 characters to 255 characters on [POST Submit Prescription Data](https://api-docs.lifepack.id/#01382ce2-fb36-45cd-9077-a31495d47413) endpoint.

## 2020-12-16
- **[Breaking Changes]** Partner that sent "address" entity empty on [POST Submit Prescription Data](https://api-docs.lifepack.id/#01382ce2-fb36-45cd-9077-a31495d47413) endpoint should notice that the `address` entity on [GET Subscription Detail](https://api-docs.lifepack.id/#16595cf9-dfe3-4b83-a319-5e61d12464f9) endpoint will have value of empty object (`{}`) until user has set the address in the link given by SMS/notification at `pending_address` status. This happens to avoid delivery price showing up before user has set the address.
- Adjust explanation on `payment` entity, add [`method`, `logo`, `account_number`] and change `expired_at` documentation on [GET Subscription Detail](https://api-docs.lifepack.id/#16595cf9-dfe3-4b83-a319-5e61d12464f9) endpoint.

# Overview
## Lifepack Open API Description

LifepackPartner is a project used to describe and document RESTful APIs.

## Partner Account Types

Currently, there is two different partner account types available for partners to apply:
1. Standard Partner Account - Partner who's applying this kind of account should have their customer coordinate address data to send to us while sending [Submit Prescription Data](https://api-docs.lifepack.id/?version=latest#01382ce2-fb36-45cd-9077-a31495d47413) requests and also they should have their own payment system.
2. Payment on Us Partner Account - Partner who applying this kind of account are the ones that still don't have their own payment system. Sending patient address coordinates while sending [Submit Prescription Data](https://api-docs.lifepack.id/?version=latest#01382ce2-fb36-45cd-9077-a31495d47413) requests are also optional.

## Bussiness Flow

### Subscription Creation Flow

![Subscription Flow](https://drive.google.com/uc?export=view&id=1PCmQw8yN6hPYXVll3Mjr_iVn7cJnHDpx)

### Payment Flow

Currently, there are two payment flow available to use on our system. The default payment flow and payment flow with payment on us option. If your system or existing data doesn't have user's address coordinate picker and payment system, you can apply for payment on us option to be enabled by contacting our business team.

#### Default Payment Flow

The default payment flow starts after the prescription has reviewed and approved by our pharmacists. You can directly hit our [Change Payment Status to Paid](https://api-docs.lifepack.id/?version=latest#60c7c2e6-5e27-47d9-9713-7b898a1f6f16) endpoint after your customer's payment is already paid and verified in your system.

![Payment Flow](https://drive.google.com/uc?export=view&id=1yp8QoGvr5vK6DiuuKHt4kJV_w7SsWDoR)

#### Payment on Us Flow

The payment on us flow also starts after the prescription has reviewed and approved by our pharmacists. But, the entire process on address picking will happen in our system. You can just listen to webhook callback from us for the subscription status updates.

![Payment on Us Flow](https://drive.google.com/uc?export=view&id=1BQ-iEc2-b8UYNHXco6HSg5nfzNB4dz2j)

## UX Guideline

### Registration Flow

![Registration Flow](https://drive.google.com/uc?export=view&id=1xC6ypOAh5hAq4sizGogpF8zkz697ENsu)

### Create Digital Prescription Flow

![Create Digital Prescription Flow 1](https://drive.google.com/uc?export=view&id=1GtZR5rYW5HJ1vFwyc-1xxoLMrPf5una0)

![Create Digital Prescription Flow 2](https://drive.google.com/uc?export=view&id=1CV_GqYcUpOwXJpZQpMStcuTevPDkyY17)

![Create Digital Prescription Flow 3](https://drive.google.com/uc?export=view&id=1x6jfnpqq-U_uBMq5JSa9JbfqIEqD6vkO)

### Create Photo Prescription Flow

![Create Photo Prescription Flow 1](https://drive.google.com/uc?export=view&id=12w_cpriIa3QiOME4p6_mFl7RkSVw8QYl)

![Create Photo Prescription Flow 2](https://drive.google.com/uc?export=view&id=1Zpcy4AJaa4CnEodos9SwW4Z4fGRZyfuS)

# Features

## Easy to Integrate API

- Our RESTful API’s enable our partners to integrate to our solution seamlessly;
- Lifepack API support: Prescription, Subscription, Payment, Patient, Product.

## Dashboard

- Lifepack provides a portal for our partners to see all prescription history as well as analytics of their shipment and consumption activities;

# Setting Up

Once a partner has registered, it will have an access to our sandbox environment. Lifepack partner dashboard will also be accessible.

## Getting Notification

LIfepack allows partners to receive realtime notifications about Lifepack related information, by configuring a endpoint url on the Lifepack Partner Dashboard.

We are sending notifications to Webhook URL. This endpoint will only be triggered if there are status changes to existing subscription. Please refer to [subscription status reference section](https://api-docs.lifepack.id/?version=latest#subscription-status) for which statuses are sent in the notification.

Once configured, Lifepack will send a HTTP POST payload to the url, containing detail about specific event which can be seen in the notification payload section.

**Configuring the Endpoint URL**

- To setup an Endpoint URL on Lifepack, head over to the **SETTINGS** tab on the sidebar, and edit the values on **WEBHOOK URL**.
- Save the notification URL using the **Submit** button. The notification URL can be modified anytime from the settings page.

## Notification Payload

Example Payload:

```json
{
  "subscription_id": 1791,
  "status": "payment_order",
  "patient": {
    "id": "652",
    "name": "Jono Hipertensi",
    "phone_number": "+628537333452",
    "address": {
      "id": 4849,
      "default": false,
      "latitude": -6.406614,
      "longitude": 106.822083,
      "first_line": "Telaga Golf",
      "second_line": "Jl. Hr. Rasuna Sahid",
      "postal_code": "16412",
      "note": "Graha Irama",
      "street_name": " ",
      "province": "West Java",
      "city": "Depok City",
      "district": "Sukmajaya",
      "sub_district": null
    }
  },
  "total_payment": 356250,
  "products": [
    {
      "id": 1179,
      "name": "VERAPAMIL HCL",
      "qty": 2,
      "consumption_day": 5,
      "total_qty": 10
    },
    {
      "id": 1013,
      "name": "SHAROX 500 MG",
      "qty": 2,
      "consumption_day": 5,
      "total_qty": 10
    }
  ],
  "timestamp": "2020-08-27 17:49:56"
}
```

### Payload Description

| Parameter       | Description                                                                                                                            |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
| subscription_id | Subscription ID of the notification                                                                                                    |
| patient         | `object` Please refer to [patient entity](https://api-docs.lifepack.id/#patient-entity)                                                |
| status          | Refer to [subscription status reference section](https://api-docs.lifepack.id/?version=latest#subscription-status) for possible values |
| total_payment   | Amount of the total payment for current subscription                                                                                   |
| timestamp       | `string` Last update time                                                                                                              |
|                 | Date format `YYYY-MM-DD HH:mm:ss`                                                                                                      |

### Product Entity

| id              | Product ID                              |
|-----------------|-----------------------------------------|
| name            | Product name                            |
| qty             | Quantity taken per day                  |
| consumption_day | Total days user should taking medicine  |
| total_qty       | Total quantity of product given to user |

## Error Code and Message

### Description Of Usual Server Responses (HTTP Codes)

- `200 OK` - the request was successful (some API calls may return 201 instead).
- `201 Created` - the request was successful and a resource was created.
- `202 Accepted` - the request was accepted and enqueue for processing later.
- `204 No Content` - the request was successful but there is no representation to return (i.e. the response is empty).
- `400 Bad Request` - the request could not be understood or was missing required parameters.
- `401 Unauthorized` - authentication failed.
- `403 Forbidden` - access denied.
- `402 Payment Required` - payment is required.
- `404 Not Found` - resource was not found.
- `410 Gone` - the resource has been expired.
- `422 Unprocessable Entity` - i.e. validation errors.
- `500 Internal Server Error` - Bad bad bad.
- `503 Service Unavailable` - service is temporary unavailable (e.g. scheduled Platform Maintenance). Try again later.

### Error Structure

Aside from the `4XX` and `5XX` error HTTP Headers, we have an unified error structure:

```
{
  "error_code": "INTERNAL_SERVER_ERROR",
  "message": "Internal Server Error"
}
```

This means that, if you get an `4XX` or `5XX` errors, you can utilize your system to log or display the error message to the user. Possible error codes will be explained in each endpoints.

# Reference

## Subscription Status

| Status                | Description                                                                     | Status appears on subscription detail? | Will receive notification? |
|-----------------------|---------------------------------------------------------------------------------|----------------------------------------|----------------------------|
| in_review             | Prescription is under review (products and total payment still not exists)      | ✅                                      | ❌                          |
| prescription_approved | Prescription approved by pharmacist                                             | ✅                                      | ✅                          |
| prescription_adjusted | Prescription is adjusted, partner should update prescription detail information | ❌                                      | ✅                          |
| order_cancelled       | Prescription cancelled by pharmacist                                            | ✅                                      | ✅                          |
| order_expired         | Order is not continued within the time specified at `expired_at`                | ✅                                      | ✅                          |
| prescription_rejected | Prescription is rejected by admin                                               | ✅                                      | ✅                          |
| pending_address       | User need to update address                                                     | ✅                                      | ✅                          |
| payment_order         | Prescription is approved by admin and ready to be charged                       | ✅                                      | ✅                          |
| waiting_for_payment   | User already selected payment method (only for payment on us partner type)      | ✅                                      | ✅                          |
| payment_successful    | Order has successfully paid by user                                             | ✅                                      | ✅                          |
| payment_expired       | Payment has expired (only for payment on us partner type)                       | ✅                                      | ✅                          |
| payment_failed        | Payment has failed (only for payment on us partner type)                        | ✅                                      | ✅                          |
| order_processed       | Pharmacist is preparing the order                                               | ✅                                      | ✅                          |
| waiting_for_pickup    | Package is ready to ship, waiting the courier to pick up                        | ✅                                      | ✅                          |
| picked_up             | Package is picked up by courier                                                 | ✅                                      | ✅                          |
| on_delivery           | Package is on delivery to customer address                                      | ✅                                      | ✅                          |
| delivered             | Package has already delivered to customer address                               | ✅                                      | ✅                          |
| delivery_failed       | Package delivery has failed                                                     | ✅                                      | ✅                          |
| active                | User click confirm button in lifepack app/automatically after 24 h delivered    | ✅                                      | ✅                          |
| inactive              | Medication schedule ended                                                       | ✅                                      | ✅                          |

# Authorization

For the authorization headers for authenticating the requests, please refer to our [Authorization](https://api-docs.lifepack.id/?version=latest#authorization-header) section.

### Link to further [documentation](https://www.postman.com/healthcare-demo/workspace/virtual-care/documentation/16901628-2bb86bac-11c6-4061-ae75-c0b6e3141693) within Postman
