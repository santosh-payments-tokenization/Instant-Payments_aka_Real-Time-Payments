# SEPA Instant Payments (SCT Inst) Knowledge Base

> A personal reference and investigation knowledge base covering **SEPA Instant Credit Transfer (SCT Inst)**, relevant European payment infrastructure, EPC documentation, ISO 20022 status/reason codes, and payment investigation/reconciliation examples.

---

## Table of Contents

- [1. Overview](#1-overview)
- [2. SCT Inst Background](#2-sct-inst-background)
  - [2.1 EU / EEA / Europe Context](#21-eu--eea--europe-context)
  - [2.2 Eurosystem and Market Infrastructure](#22-eurosystem-and-market-infrastructure)
  - [2.3 EPC / SEPA Schemes and Services](#23-epc--sepa-schemes-and-services)
- [3. Instant Payment Regulation (IPR)](#3-instant-payment-regulation-ipr)
- [4. EPC SCT Inst Rulebook](#4-epc-sct-inst-rulebook)
- [5. EPC SCT Inst Implementation Guidelines](#5-epc-sct-inst-implementation-guidelines)
- [6. ISO 20022 External Codes](#6-iso-20022-external-codes)
  - [6.1 Payment Transaction Status Codes](#61-payment-transaction-status-codes)
  - [6.2 Status Reason Codes](#62-status-reason-codes)
- [7. SCT Inst Investigation Notes](#7-sct-inst-investigation-notes)
  - [7.1 Reject Scenarios](#71-reject-scenarios)
  - [7.2 Rejection Summary](#72-rejection-summary)
- [8. Reconciliation Examples](#8-reconciliation-examples)
- [9. Transaction Investigation Examples](#9-transaction-investigation-examples)
- [10. Creditor Agent BIC Investigation](#10-creditor-agent-bic-investigation)
- [11. Reference Links](#11-reference-links)
- [12. Repository Usage](#12-repository-usage)

---

# 1. Overview

This repository captures practical reference material relating to **SEPA Instant Credit Transfer (SCT Inst)** and ISO 20022 payment processing.

The source workbook brings together:

- European SCT Inst background and ecosystem notes.
- Eurosystem infrastructure references including **T2, T2S and TIPS**.
- A reference to **Pontes**, described in the workbook as a DLT bridge between blockchain and TARGET2 services.
- Private CSM references including **EBA STEP2, EBA RT1 and Equens Worldline**.
- EPC SCT Inst rulebook and implementation guideline references.
- ISO 20022 external payment status and reason codes.
- `pacs.002` rejection investigation scenarios.
- Reconciliation and transaction-status investigation examples.
- Creditor Agent BIC-related failure analysis.

The purpose of this knowledge base is to make the workbook content easier to navigate and reference from GitHub Pages.

[Back to top](#table-of-contents)

---

# 2. SCT Inst Background

## 2.1 EU / EEA / Europe Context

The workbook places SCT Inst within the wider European payments environment and notes:

- **27 members of the EU**.
- **3 members of the EEA**.
- **UK and Switzerland**.
- **Microstates**.
- Other Eastern European countries.
- A total reference of **41 members** in the workbook notes.

This section provides contextual background for understanding the geographical scope surrounding European payment schemes and market infrastructures.

## 2.2 Eurosystem and Market Infrastructure

The workbook references the **Eurosystem (ECB + Central Banks)** and the following infrastructure:

| Infrastructure / Topic | Workbook Reference |
|---|---|
| T2 | TARGET2 Services |
| T2S | TARGET2 Services |
| TIPS | TARGET2 Services |
| Pontes | DLT bridge between blockchain and TARGET2 services |
| EBA STEP2 | Private CSM |
| EBA RT1 | Private CSM |
| Equens Worldline | Private CSM |

## 2.3 EPC / SEPA Schemes and Services

The workbook identifies the following schemes/services in the EPC-SEPA context:

- **SCT**
- **SDD (Core & B2B)**
- **SCT Inst**
- **OCT**
- **RTP**
- **VoP**

The workbook focuses primarily on **SCT Inst**, including its rulebook, implementation guidelines, status codes, reject scenarios and reconciliation examples.

[Back to top](#table-of-contents)

---

# 3. Instant Payment Regulation (IPR)

The workbook contains a dedicated reference to the **Instant Payment Regulation (IPR)** and notes that there are **mainly four requirements**, without enumerating those requirements in the workbook.

**Reference location:**

<https://www.ecb.europa.eu/paym/retail/instant_payments/html/instant_payments_regulation.en.html>

This link should be used alongside the workbook when reviewing regulatory requirements applicable to instant payments.

[Back to top](#table-of-contents)

---

# 4. EPC SCT Inst Rulebook

The workbook references the following SCT Inst rulebook:

| Item | Details |
|---|---|
| SEPA Scheme | SCT Inst |
| Rulebook | 2025 SEPA Instant Credit Transfer Rulebook |
| Version | 1.2 |
| Document Reference | EPC004-16 |
| Effective Date | 30 September 2026 |

**EPC Rulebook location:**

<https://www.europeanpaymentscouncil.eu/search?kb%5B0%5D=tags%3A171>

The rulebook is a key reference point for understanding the scheme rules governing SCT Inst processing.

[Back to top](#table-of-contents)

---

# 5. EPC SCT Inst Implementation Guidelines

The workbook references the following SCT Inst implementation guideline:

| Item | Details |
|---|---|
| SEPA Scheme | SCT Inst |
| Implementation Guideline | SEPA Instant Credit Transfer Inter-PSP Implementation Guidelines |
| Version | 2025 version 1.0 |
| Document Reference | EPC122-16 |
| Effective Date | 5 October 2025 |

**EPC Implementation Guidelines location:**

<https://www.europeanpaymentscouncil.eu/search?kb%5B0%5D=tags%3A171&kb%5B1%5D=type%3A86>

These guidelines are used as a technical reference for implementing SCT Inst messages and validating scheme-specific requirements.

[Back to top](#table-of-contents)

---

# 6. ISO 20022 External Codes

The workbook references the ISO 20022 external code sets:

<https://www.iso20022.org/catalogue/additional-content-messages/external-code-sets>

The following payment transaction status and status reason codes are captured in the workbook.

## 6.1 Payment Transaction Status Codes

| Code Set | Code | Name | Meaning / Workbook Definition |
|---|---|---|---|
| ExternalPaymentTransactionStatus1Code | `ACSC` | AcceptedSettlementCompletedDebitorAccount | Settlement completed. The workbook notes that it can be used by a market infrastructure or account servicer to report that the transaction account entry has been completed, subject to bilateral agreement. |
| ExternalPaymentTransactionStatus1Code | `RJCT` | Rejected | Payment instruction has been rejected. |

## 6.2 Status Reason Codes

| Code | Code Name | Workbook Meaning / Investigation Context |
|---|---|---|
| `AB06` | TimeoutInstructedAgent | Transaction stopped due to timeout at the Instructed Agent. |
| `AM02` | NotAllowedAmount | Transaction/message amount is greater than the allowed maximum. |
| `AM05` | Duplication | Duplicate transaction. |
| `FF01` | InvalidFileFormat | File format incomplete or invalid. |
| `RC01` | BankIdentifierIncorrect | Bank identifier code has an incorrect format. |

The workbook also references EPC guidance on reason codes for SCT Inst R-transactions:

<https://www.europeanpaymentscouncil.eu/sites/default/files/kb/file/2026-09/EPC059-18%20v7.1%20Guidance%20on%20Reason%20Codes%20for%20SCT%20Inst%20R-transactions.pdf>

[Back to top](#table-of-contents)

---

# 7. SCT Inst Investigation Notes

## 7.1 Reject Scenarios

The workbook records the following `pacs.002` rejection scenarios and observed causes:

| Reject / Result | Investigation Observation |
|---|---|
| `FF01` | Structural validation failure caused by missing mandatory elements, for example **Total Interbank Settlement Amount**. |
| `RC01` | BIC validation failed against RegEx because of trailing white spaces / Creditor Agent BIC formatting. |
| `AM02` | Maximum amount was configured as **100K**, while the EPC implementation guideline referenced in the workbook permits a higher amount. |
| `FF01` | Special character `&` in the Debtor name was not allowed under the EPC IG character-set rule referenced in the workbook. |
| `AB06` | Timeout caused by an incorrect time setting in the configuration; maximum execution time was exceeded. |
| `AM05` | Duplicate payment caused by retry being enabled in configuration. |
| `VOP_NOMATCH` | VoP no-match scenario recorded in the investigation data. |

These examples demonstrate how payment rejections may originate from **schema/structural validation, reference-data quality, configuration, timeout, duplicate-processing and verification checks**.

## 7.2 Rejection Summary

The workbook records **68 total rejection / exception observations** in its summary.

| Reject Reason | Number of Rejections |
|---|---:|
| `FF01` | 10 |
| `RC01` | 18 |
| `AM02` | 9 |
| `AB06` | 14 |
| `AM05` | 2 |
| `VOP_NOMATCH` | 9 |
| No reason code | 6 |
| **Total** | **68** |

This distribution can be used as a quick reference when prioritising investigation themes.

[Back to top](#table-of-contents)

---

# 8. Reconciliation Examples

The workbook contains reconciliation examples linking accounting entries with payment-message status.

| Entry Ref | Related Message ID | Reconciliation Status | `pacs.002` Status | Reason | Investigation Note |
|---|---|---|---|---|---|
| `E-90189` | `PIPT-90189` | `PDNG` | `ACSC` | — | No confirmation from CSM; status unknown. |
| `E-90280` | `PIPT-90280` | `BOOK` | `RJCT` | `AB06` | Settled despite `pacs.002` reject; workbook flags timeout/retry for investigation. |

These examples highlight an important investigation principle:

> A payment-message status should be reconciled with the accounting/settlement position rather than reviewed in isolation.

Potential inconsistencies between a `pacs.002` status and ledger/reconciliation status need to be investigated using the related message ID and available transaction evidence.

[Back to top](#table-of-contents)

---

# 9. Transaction Investigation Examples

The workbook also includes transaction-level examples in which the same message ID appears with different statuses.

| Message ID | Creditor Agent BIC | Amount | Currency | Market | Status | Reason |
|---|---|---:|---|---|---|---|
| `PIPT-90281` | `BNPAFRPP` | 2,891.00 | EUR | PT | `RJCT` | `AB06` |
| `PIPT-90281` | `BNPAFRPP` | 2,891.00 | EUR | PT | `ACSC` | — |
| `PIPT-90261` | `MONTPTPL ` | 3,184.80 | EUR | PT | `RJCT` | `RC01` |
| `PIPT-90261` | `MONTPTPL ` | 3,184.80 | EUR | PT | `ACSC` | — |

The examples are useful for investigating:

- Multiple status events for the same message.
- Timeout/retry scenarios.
- BIC formatting issues.
- The difference between rejection events and eventual successful settlement status.
- Reconciliation of technical message events against the final payment state.

[Back to top](#table-of-contents)

---

# 10. Creditor Agent BIC Investigation

The workbook contains a separate Creditor Agent BIC investigation sheet. The BIC values in that sheet are masked.

The rejection summary is consistent with the main investigation data:

| Reject Reason | Rejections | Main Investigation Theme |
|---|---:|---|
| `FF01` | 10 | Structural / mandatory-element validation |
| `RC01` | 18 | Creditor Agent BIC format / trailing whitespace |
| `AM02` | 9 | Configured maximum amount |
| `AB06` | 14 | Timeout / maximum execution time |
| `AM05` | 2 | Duplicate processing / retry configuration |
| `VOP_NOMATCH` | 9 | VoP no-match |
| No reason code | 6 | No reason code found |

The BIC examples in the workbook are intentionally represented as `maskedXXX`.

[Back to top](#table-of-contents)

---

# 11. Reference Links

| Reference | URL |
|---|---|
| ECB / Instant Payment Regulation | <https://www.ecb.europa.eu/paym/retail/instant_payments/html/instant_payments_regulation.en.html> |
| EPC SCT Inst Rulebook Search | <https://www.europeanpaymentscouncil.eu/search?kb%5B0%5D=tags%3A171> |
| EPC SCT Inst Implementation Guidelines Search | <https://www.europeanpaymentscouncil.eu/search?kb%5B0%5D=tags%3A171&kb%5B1%5D=type%3A86> |
| ISO 20022 External Code Sets | <https://www.iso20022.org/catalogue/additional-content-messages/external-code-sets> |
| EPC SCT Inst R-transaction Reason Code Guidance | <https://www.europeanpaymentscouncil.eu/sites/default/files/kb/file/2026-09/EPC059-18%20v7.1%20Guidance%20on%20Reason%20Codes%20for%20SCT%20Inst%20R-transactions.pdf> |

[Back to top](#table-of-contents)

---

# 12. Repository Usage

A simple GitHub repository structure could be:

```text
SEPA-Payments/
│
├── README.md
├── SEPA_Payments.xlsx
└── docs/
    └── additional-notes/
```

Suggested use of this repository:

1. Use **README.md** as the main GitHub Pages learning/reference page.
2. Keep **SEPA_Payments.xlsx** as the detailed working workbook.
3. Add future notes or diagrams under a `docs/` directory.
4. Update the README when new EPC rulebook versions, implementation guidelines or investigation scenarios are added to the workbook.

---

## Scope Note

This README is a structured representation of the information contained in the accompanying `SEPA_Payments.xlsx` workbook. It is intended as a personal learning and reference knowledge base. For implementation decisions, always consult the applicable current scheme rulebooks, implementation guidelines and official standards documentation.

---

**Topics:** `SEPA` · `SCT-Inst` · `ISO-20022` · `pacs.002` · `EPC` · `TIPS` · `Payments` · `Reconciliation` · `Payment-Investigation`
