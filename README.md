# 不想寫程式時每次欄位都一個一個打，所以做了這個HTML小工具

# Oracle CREATE TABLE 欄位提取器

一個輕量、免安裝的 Oracle SQL 輔助工具，可從 `CREATE TABLE` 建表語法中自動提取欄位名稱，並產生逗號分隔的欄位清單。

## 專案簡介

在開發 Oracle SQL 或 PL/SQL 程式時，有時需要從既有的 `CREATE TABLE` 語法中取得所有欄位名稱，用於撰寫 `SELECT`、`INSERT`、`UPDATE` 或其他 SQL 語句。

如果欄位數量較多，手動複製不僅耗時，也容易遺漏欄位。

因此製作這個小工具，透過瀏覽器解析 Oracle `CREATE TABLE` 語法，自動提取欄位名稱，減少重複性的手動操作。

本工具使用純 HTML、CSS 與 JavaScript 開發，不需要安裝額外套件，也不需要連接資料庫。

## 功能特色

- **自動提取欄位**：解析 `CREATE TABLE` 語法並取得欄位名稱。
- **註解過濾**：自動忽略單行註解（`--`）與區塊註解（`/* */`）。
- **排除約束條件**：自動排除 `CONSTRAINT`、`PRIMARY KEY`、`FOREIGN KEY`、`UNIQUE`、`CHECK` 等定義。
- **大小寫轉換**：可選擇將欄位名稱統一轉換為大寫。
- **輸出格式設定**：支援逗號分隔及逐行排列。
- **一鍵複製**：直接將提取結果複製到剪貼簿。
- **範例載入**：提供範例 SQL，方便快速測試。
- **響應式介面**：可依不同螢幕尺寸調整版面。

## 使用方式

本工具不需要安裝，下載後即可使用。

1. 下載或 Clone 此 Repository。
2. 使用 Chrome 或 Microsoft Edge 開啟 `index.html`。
3. 將 Oracle `CREATE TABLE` SQL 貼到左側輸入框。
4. 點擊「提取欄位」。
5. 右側會顯示提取結果。
6. 點擊「複製結果」，即可複製欄位清單。

## 使用範例

### 輸入 SQL

```sql
CREATE TABLE T0NGAA22
(
    CO            VARCHAR2(2),
    DIV           VARCHAR2(1),
    SALID         VARCHAR2(1),
    CUNO          VARCHAR2(6),
    EMPNM         VARCHAR2(30),
    DUT           VARCHAR2(30),
    TEL           VARCHAR2(20),
    CLPHN         VARCHAR2(20),
    FAX           VARCHAR2(20),
    EMAILBX       VARCHAR2(40),
    CONSTRAINT PK_T0NGAA22 PRIMARY KEY (CO, DIV, SALID, CUNO)
);
```

### 輸出結果

```text
CO,DIV,SALID,CUNO,EMPNM,DUT,TEL,CLPHN,FAX,EMAILBX
```

## 專案結構

```text
oracle-create-table-column-extractor/
│
├── index.html
└── README.md
```

目前將 HTML、CSS 與 JavaScript 整合在單一 HTML 檔案中，方便下載、部署及維護。

## 使用技術

- HTML5
- CSS3
- JavaScript

不需要前端框架、第三方套件或後端

## 瀏覽器支援

目前以現代桌面瀏覽器為主要使用環境：

- Google Chrome
- Microsoft Edge

介面支援響應式排版，可依螢幕尺寸調整顯示方式。

## 資料安全與隱私

所有 SQL 解析作業皆在用戶端的瀏覽器中完成。

輸入的 SQL 不會上傳至任何伺服器或外部服務。

## 注意事項

本工具主要用於一般 Oracle `CREATE TABLE` 欄位定義的提取，並非完整的 Oracle SQL Parser。

提取結果建議在實際使用前再次確認，避免特殊 SQL 語法造成解析結果不完整。

## License

本專案採用 MIT License 開源授權。

你可以自由使用、複製、修改及散布本專案的程式碼，包含商業用途，但須保留原始著作權聲明及授權條款。

# Oracle CREATE TABLE Column Extractor

A lightweight browser-based tool for extracting column names from Oracle `CREATE TABLE` statements.

## Overview

When working with Oracle databases, I sometimes need to extract all column names from a `CREATE TABLE` script for use in `SELECT` statements, PL/SQL procedures, or other SQL operations.

Instead of copying column names one by one, this tool automatically parses the table definition and generates a comma-separated column list.

The tool runs entirely in the browser. No installation, database connection, or backend service is required.

## Features

- **Automatic Column Extraction** – Extract column names from Oracle `CREATE TABLE` statements.
- **Comment Handling** – Ignore single-line (`--`) and block (`/* */`) comments.
- **Constraint Filtering** – Exclude table constraints such as `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, and `CHECK`.
- **Case Conversion** – Optionally convert all column names to uppercase.
- **Output Formatting** – Generate comma-separated or line-separated column lists.
- **Copy to Clipboard** – Copy the extracted result with one click.
- **Sample SQL** – Load a built-in example to test the tool.

## Getting Started

No installation or additional dependencies are required.

1. Download or clone this repository.
2. Open `index.html` in your browser.
3. Paste an Oracle `CREATE TABLE` statement into the input panel.
4. Click **Extract Columns**.
5. Copy the generated column list from the output panel.

## Example

### Input

```sql
CREATE TABLE EMP
       (EMPNO NUMBER(4) NOT NULL,
        ENAME VARCHAR2(10),
        JOB VARCHAR2(9),
        MGR NUMBER(4),
        HIREDATE DATE,
        SAL NUMBER(7,2),
        COMM NUMBER(7,2),
        DEPTNO NUMBER(2),
        CONSTRAINT PK_EMP PRIMARY KEY (EMPNO),  
        CONSTRAINT FK_DEPTNO FOREIGN KEY (DEPTNO) REFERENCES DEPT (DEPTNO)          
        );
```

### Output

```text
EMPNO,ENAME,JOB,MGR,HIREDATE,SAL,COMM,DEPTNO
```

## Project Structure

```text
oracle-create-table-column-extractor/
│
├── index.html
└── README.md
```

The application is implemented in a single HTML file, including its CSS styles and JavaScript logic.

## Technologies

- HTML5
- CSS3
- Vanilla JavaScript

No frameworks, external libraries, or backend services are used.

## Compatibility

Designed for modern desktop browsers, including:

- Google Chrome
- Microsoft Edge

The interface also supports smaller screen sizes through responsive CSS.

## Privacy

All SQL parsing is performed locally in the browser.

The SQL content entered by the user is not uploaded to any server or external service.

## Notes

This tool is intended for extracting column names from standard Oracle `CREATE TABLE` definitions. It is not a complete Oracle SQL parser.

Please verify the extracted result before using it in production SQL scripts.

## License

This project is licensed under the MIT License.

You are free to use, copy, modify, and distribute the source code, including for commercial purposes, provided that the original copyright notice and license terms are retained.
