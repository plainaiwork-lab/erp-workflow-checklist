# ERP workflow checklist: five decisions before requesting a quote

An ERP scope is easier to estimate when it describes a workflow, its data and its failure cases. This checklist is a starting point for small teams comparing standard configuration, integration and custom development.

## 1. Choose one workflow

Start with a specific path: order received → SKU checked → stock reserved → ready to pick. Record who owns each step, which tool they use and where manual copying occurs.

- [ ] Define the start and end of the first release.
- [ ] Describe out-of-stock items, cancellations and partial fulfilment.
- [ ] Name a person who can decide unresolved business rules.

## 2. Assign data ownership

For products, customers, prices and stock, identify the authoritative source and who may change it. Two systems should not silently overwrite the same field.

- [ ] Provide anonymized sample records with stable identifiers.
- [ ] List duplicate records, missing fields and incompatible formats.
- [ ] Agree on migration validation and reconciliation responsibilities.

## 3. Compare implementation routes

| Route | Useful when | Questions to resolve |
| --- | --- | --- |
| Standard ERP configuration | Existing features match the workflow | Which gaps can the team accept? |
| Integration with current tools | Existing systems should remain | Who owns each field, retry and reconciliation? |
| Custom development | Essential rules do not fit available configuration | Who maintains the system and tests future changes? |

Write exclusions alongside inclusions. Accounting, historical migration and management reports should not be assumed to be included simply because they relate to ERP.

## 4. Define acceptance tests before building

The examples below are proposed tests, not results from a deployed implementation.

| Scenario | Expected outcome to agree |
| --- | --- |
| The same external order is delivered twice | One business order and one effective stock reservation |
| An order contains an unknown SKU | A visible exception; no silent substitution or shipment |
| A reservation is cancelled | Stock is released according to the agreed state rules |
| Two orders compete for the last item | The agreed allocation rule prevents unintended overselling |
| A connection fails after a remote write | Recovery checks the existing outcome before repeating the effect |
| An unauthorized user changes stock | The action is rejected and relevant audit information is retained |

A duplicate-request check alone does not guarantee correctness. Agree on the identifier's scope, atomic stock updates, retry behavior and reconciliation for partial failures.

## 5. Prepare a useful quote brief

Include the workflow diagram, existing tools, user roles, expected volume, anonymized samples, exception rules, acceptance tests and deployment constraints. Ask vendors to separate licensing, migration, integration, testing, training, support and later changes.

A small first release is useful only if its boundary is explicit. Name what must work on launch day and what will be evaluated later.

## Copyable brief

- Workflow and business owner:
- Systems retained:
- Authoritative data sources:
- Volume and concurrency assumptions:
- Rules and exceptions:
- In scope / out of scope:
- Acceptance tests:
- Migration and rollback approach:
- Training and support responsibilities:

Prepared by **PlainAIWork**, which works on ERP development and system integration. Learn more: https://plainaiwork.com
