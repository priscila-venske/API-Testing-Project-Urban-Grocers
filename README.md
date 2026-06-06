# API Testing Project – Urban Grocers

> Software integration testing project applied to the **Urban Grocers** backend ecosystem. This project focuses on complete endpoint validation, verification of request payloads, data constraint checks, and systematic edge-case testing for critical business microservices.

`API Testing` `Integration Testing` `Boundary Value Analysis (BVA)` `Equivalence Partitioning` `Negative Testing` `JSON Payload Validation` `Status Code Verification`

---

## Objective
Planning, documentation, and execution of API tests for newly implemented backend features in the Urban.Grocers platform, focusing on functional validation, business rules verification, and API response analysis.

## Overview

This repository provides a comprehensive artifact log documenting an exhaustive manual and automated integration testing lifecycle conducted on the **Urban Grocers** web platform backend. Testing activities targeted specific API endpoints controlling product kit composition and rapid delivery calculation matrices.

| Item | Detail |
|---------------------------------|---------------------------------------------|
| **Platform Ecosystem** | Urban Grocers — Microservices API Web |
| **Testing Classification** | Integration, Boundary Value & Negative Testing |
| **Total Test Cases Executed** | 67 |
| **Passed Validation Items** | 27 |
| **Bugs / Defects Logged (FAILED)** | 40 |
| **Blocked / Interrupted Items** | 0 |

---

## Tools Used
* **Postman** (API Execution & Scripting)
* **Google Chrome DevTools** (Network Inspection & Console)
* **Jira** (Bug Tracking Structure)
* **Microsoft Excel / Google Sheets** (Test Data Sheet Management)

---

## Testing Scope & Test Cases

###  Endpoint 1 — `POST /api/v1/cards/{id}/kits`
Validation of adding individual or bulk products to predefined customer kits. Tests ensure maximum item threshold checks, proper data type parameters, and response behavior when receiving invalid string data inside numerical formats.

| ID | Brief Description | Status |
|----|-------------------|--------|
| **P1** | Send POST request to insert a valid item into a kit | ✅ PASSED |
| **P2** | Send POST request to update the quantity of an existing item | ✅ PASSED |
| **P3** | Send POST request with item ID set to `null` | [❌ FAILED](https://drive.google.com/file/d/1XO5lyzjgXGrX54IxyoTWbO7hnErzV_5D/view?usp=drive_link) |
| **P4** | Send POST request with item ID set to `" "` (empty string) | [❌ FAILED](https://drive.google.com/file/d/1rz5vhwfcXchMPzMpjJRNR3kzaho7IjmK/view?usp=drive_link) |
| **P5** | Send POST request with item ID set to a `"string"` type value | [❌ FAILED](https://drive.google.com/file/d/1E1hmD7-xupFwgvG3CXYkBI5kyWc-v2i2/view?usp=drive_link) |
| **P6** | Send POST request with item ID containing special characters | [❌ FAILED](https://drive.google.com/file/d/1DGN_20MZ3VgvfEgH6AgGBXck0HT531Uz/view?usp=drive_link) |
| **P7** | Send POST request with an extremely long integer value for item ID | [❌ FAILED](https://drive.google.com/file/d/1hM70oLlylDtnWVtDwLweRg4WntOf4Ssl/view?usp=drive_link) |
| **P8** | Send POST request with item ID set to a negative integer | [❌ FAILED](https://drive.google.com/file/d/1GLZ8e4zXSqAhDg088UW78Q2pZ2tjg99a/view?usp=drive_link) |
| **P9** | Send POST request with `quantity` parameter set to `null` | [❌ FAILED](https://drive.google.com/file/d/1VKl7KN0TTJlg6NgnzibjsRfMeGmwcd-d/view?usp=drive_link) |
| **P10**| Send POST request with `quantity` parameter set to `""` (empty) | [❌ FAILED](https://drive.google.com/file/d/1OKSx8_8uv0_jprCDl1PvPV7FPideYJWW/view?usp=drive_link) |
| **P11**| Send POST request with `quantity` parameter set to a `"string"` value | [❌ FAILED](https://drive.google.com/file/d/1qoXYRrQ4DbEQCKbgRBAwu6-Cb8fo0JIe/view?usp=drive_link) |
| **P12**| Send POST request with `quantity` parameter containing special characters | [❌ FAILED](https://drive.google.com/file/d/1aWmeisenTYVjpSaQysYMa90l9XOsRD0u/view?usp=drive_link) |
| **P13**| Send POST request with an extremely long value for `quantity` | [❌ FAILED](https://drive.google.com/file/d/1CPerRdoVyM_mrbScAoSqeIBS4CyYfyvY/view?usp=drive_link) |
| **P14**| Send POST request with `quantity` parameter set to a negative number | [❌ FAILED](https://drive.google.com/file/d/1P1V52-sEj3N3tVQ-eXWkhzY-hAErabrf/view?usp=drive_link) |
| **P15**| Send POST request with an entirely empty request body | [❌ FAILED](https://drive.google.com/file/d/1BAfUAuK816vdYPFo75WGhq1LY0VEUIbG/view?usp=drive_link) |
| **P16**| Send POST request with an empty JSON object `{}` | [❌ FAILED](https://drive.google.com/file/d/1CvjTZmnWepYrBt8roxrOtvQI1CUvElS9/view?usp=drive_link) |
| **P17**| Send POST request with a JSON object containing an empty `productsList` | [❌ FAILED](https://drive.google.com/file/d/11oZN8Z5YilMLFx2GtReEKDvV5Je9f-J4/view?usp=drive_link) |
| **P18**| Send POST request containing exactly 30 bulk items | ✅ PASSED |
| **P19**| Send POST request containing exactly 31 bulk items (boundary check) | ✅ PASSED |
| **P20**| Send POST request with a kit ID different from the one originally created | ✅ PASSED |
| **P21**| Send POST request with a kit ID containing special characters | ✅ PASSED |
| **P22**| Send POST request with a kit ID set to a negative number | [❌ FAILED](https://drive.google.com/file/d/1KAFuiHo0_TWiDKt0Zva6WhjDbc4qXaZf/view?usp=drive_link)   |
| **P23**| Send POST request completely omitting request parameters | ✅ PASSED |

---

### Endpoint 2 — `POST /order-and-go/v1/delivery`
Validation of real-time rapid delivery fee calculations. Assesses the strict business operational window (`deliveryTime`), maximum items allowed per shipment (`productsCount`), and courier container weight limits (`productsWeight`).

| ID | Brief Description | Status |
|----|-------------------|--------|
| **D1** | Validate POST request when delivery cost should equal $3 | ✅ PASSED |
| **D2** | Validate POST request when delivery cost should equal $5 | ✅ PASSED |
| **D3** | Validate `deliveryTime` parameter exactly at boundary 7 hours | [❌ FAILED](https://drive.google.com/file/d/1mWH1fbg1-C968IqMfdsdAX9POVx_nGG-/view?usp=drive_link) |
| **D4** | Validate `deliveryTime` parameter exactly at boundary 8 hours | ✅ PASSED |
| **D5** | Validate `deliveryTime` parameter exactly at boundary 9 hours | ✅ PASSED |
| **D6** | Validate `deliveryTime` parameter exactly at boundary 21 hours | ✅ PASSED |
| **D7** | Validate `deliveryTime` parameter exactly at boundary 22 hours | ✅ PASSED |
| **D8** | Validate `deliveryTime` parameter exactly at boundary 23 hours | [❌ FAILED](https://drive.google.com/file/d/1yKnMxHt8S-JxJU5ELzOeukvayz8QMWuH/view?usp=drive_link) |
| **D9** | Validate `productsCount` parameter set to a negative value `-1` | [❌ FAILED](https://drive.google.com/file/d/1bCKedHr741U6teAQkYiX5oeOdWVZsMam/view?usp=drive_link) |
| **D10**| Validate `productsCount` parameter set to zero `0` | [❌ FAILED](https://drive.google.com/file/d/13OK0KbbjzYpxb7Vv-eG9M1cnKm6cMncx/view?usp=drive_link) |
| **D11**| Validate `productsCount` parameter set to `1` | ✅ PASSED |
| **D12**| Validate `productsCount` parameter set to `7` | ✅ PASSED |
| **D13**| Validate `productsCount` parameter set to `8` | ✅ PASSED |
| **D14**| Validate `productsCount` parameter set to `9` | ✅ PASSED |
| **D15**| Validate `productsCount` parameter set to `10` | ✅ PASSED |
| **D16**| Validate `productsCount` parameter set to `14` | ✅ PASSED |
| **D17**| Validate `productsCount` parameter set to `15` | ✅ PASSED |
| **D18**| Validate `productsCount` parameter set to boundary overflow value `16` | [❌ FAILED](https://drive.google.com/file/d/1LflP2BaMDRFZs1yFRivOdY0_Jr6I2Qvj/view?usp=drive_link) |
| **D19**| Validate `productsWeight` parameter set to a negative value `-1` | [❌ FAILED](https://drive.google.com/file/d/1AOUOsnx3rxWR1-oFxDkKniqQpswm3cpf/view?usp=drive_link) |
| **D20**| Validate `productsWeight` parameter set to zero `0` | [❌ FAILED](https://drive.google.com/file/d/1b0ThaAUP24Bv7bDtHkZyGiCVZSSGJHOu/view?usp=drive_link) |
| **D21**| Validate `productsWeight` parameter set to `1` | ✅ PASSED |
| **D22**| Validate `productsWeight` parameter set to `2.9` | ✅ PASSED |
| **D23**| Validate `productsWeight` parameter set to `3` | ✅ PASSED |
| **D24**| Validate `productsWeight` parameter set to `3.1` | ✅ PASSED |
| **D25**| Validate `productsWeight` parameter set to `5.9` | ✅ PASSED |
| **D26**| Validate `productsWeight` parameter set to `6` | ✅ PASSED |
| **D27**| Validate `productsWeight` parameter set to boundary overflow value `6.1` | [❌ FAILED](https://drive.google.com/file/d/1PEhMfMbzh1yf0asJl80niAC7IuNV3yBz/view?usp=drive_link) |
| **D28**| Validate `deliveryTime` parameter set to `null` | [❌ FAILED](https://drive.google.com/file/d/1CobWgZaiVUzaSbzKec6-FZCnb3c2-i5J/view?usp=drive_link) |
| **D29**| Validate `deliveryTime` parameter set to a `"string"` | [❌ FAILED](https://drive.google.com/file/d/1ag8IKMN4ZunR5AO2w0emvjtDs6Kx007V/view?usp=drive_link) |
| **D30**| Validate `deliveryTime` parameter set to special characters | [❌ FAILED](https://drive.google.com/file/d/1LKjPsiyugyXDzqXg3uabxwxXg8BvXRHl/view?usp=drive_link) |
| **D31**| Validate `deliveryTime` parameter set to an empty value `""` | [❌ FAILED](https://drive.google.com/file/d/1K72Pvyb1SBswxTS7mUwJ3H6iO6mOAoPC/view?usp=drive_link) |
| **D32**| Validate API response behavior when omitting `deliveryTime` parameter | [❌ FAILED](https://drive.google.com/file/d/1GpK1XleL5O1C-GUHRABokyKDNPAqc0Tb/view?usp=drive_link) |
| **D33**| Validate `productsCount` parameter set to `null` | [❌ FAILED](https://drive.google.com/file/d/1W9U7yfNKKMkVxYEz-PZhc-5U6s4LI_rc/view?usp=drive_link) |
| **D34**| Validate `productsCount` parameter set to a `"string"` | [❌ FAILED](https://drive.google.com/file/d/1n8a5lrBQSoFYqE3vg_d5UiN53CNvzpB7/view?usp=drive_link) |
| **D35**| Validate `productsCount` parameter set to special characters | [❌ FAILED](https://drive.google.com/file/d/1y7jo5BqGn-z-0lK0KsgIOKH7olvwwaIL/view?usp=drive_link) |
| **D36**| Validate API response behavior when omitting `productsCount` parameter | [❌ FAILED](https://drive.google.com/file/d/12qPH_7g3b_qUQrtAXTyGn9MHlR0H6SvE/view?usp=drive_link) |
| **D37**| Validate `productsCount` parameter set to an empty value `""` | [❌ FAILED](https://drive.google.com/file/d/1uAr-woq8KG7FQ7BWgNazyw9Ao6KMFcpe/view?usp=drive_link) |
| **D38**| Validate `productsWeight` parameter set to `null` | [❌ FAILED](https://drive.google.com/file/d/1UfBYLaA3W-h36bEeA5V4kx4ELGahUpPm/view?usp=drive_link) |
| **D39**| Validate `productsWeight` parameter set to a `"string"` | [❌ FAILED](https://drive.google.com/file/d/1gqnfyDgBPuotmf-zGQs8GuKtMp6u1r_I/view?usp=drive_link) |
| **D40**| Validate `productsWeight` parameter set to special characters | [❌ FAILED](https://drive.google.com/file/d/1BYI1t1R3c0MdN5TD0Tx41cAG20bnTBu3/view?usp=drive_link) |
| **D41**| Validate `productsWeight` parameter set to an empty value `""` | [❌ FAILED](https://drive.google.com/file/d/1ZWj7dvFSJMuT3No33RNbu05-L_v2tvPB/view?usp=drive_link) |
| **D42**| Validate API response behavior when omitting `productsWeight` parameter | ✅ PASSED |
| **D43**| Validate backend behavior when sending a completely empty request body | [❌ FAILED](https://drive.google.com/file/d/17vJ_GAJXlLJGskktaEwZ_V2TPTFogNKT/view?usp=drive_link) |
| **D44**| Validate backend behavior when sending an empty JSON wrapper `{}` | [❌ FAILED](https://drive.google.com/file/d/1zbXHoFCEx4HaRamkL5SHQBp8oVVSzZPh/view?usp=drive_link) |

---

## 📊 Test Execution Metrics

✅ PASSED     ░░░░░░░░░░░░░░░░░░░░  ~40.3%

❌ FAILED     ████████████████████  ~59.7%

🔒 BLOCKED    ░                     0.0%


---

## 🔍 Key Findings & Defect Behavior

The high percentage of `FAILED` scenarios highlights critical security and exception-handling flaws in the platform's backend implementation:

1. **Lack of Validation (HTTP 200 OK on Invalid Input):** Multiple fields accepted non-valid types (such as `null` or negative integers) and processed the query successfully when they should have explicitly blocked the action with an `HTTP 400 Bad Request`.
2. **Unhandled Internal Errors (HTTP 500 Server Error):** Sending special characters, whitespace, or empty strings caused fatal crashes within the API routing, revealing unhandled exceptions in data type parsing.

---

## 👤 Author
Project logged and curated as part of Quality Assurance Engineering & Platform API Validation practices.

---

## ✅ Assignment Approved
[Project Approval](https://drive.google.com/file/d/1IkzvNNxRluVvpqbgJQPiBWHj-uXUayX5/view?usp=drive_link)

---

## 📄 Licença
Este repositório é de uso educacional. Os dados e capturas de tela pertencem ao ambiente de testes do curso.


