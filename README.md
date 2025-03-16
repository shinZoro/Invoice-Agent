# Invoice-Agent

Invoice-Agent is agentic webflow using langgraph that extracts, processes, and stores invoice data using **OCR (Tesseract)** and **LLM-powered AI** (Groq LLM). It also allows users to generate and execute SQL queries on the invoice database.

## **Features**

- Extracts text from invoice images using **Tesseract OCR**.
- Uses **Open soure model llama-3.3-70b-versatile LLM** to parse extracted text into structured invoice data.
- Stores invoice details in an SQLite database.
- Provides an **LLM-powered SQL query generator** to retrieve or modify invoice data.
- Supports **automatic routing** between image processing and SQL query execution.
- Uses **LangChain and LangGraph** for efficient AI-based workflows.

---

## **Installation**

### **Prerequisites**

- Python **>=3.11**
- `pip` installed on your system
- Install dependencies:
  ```sh
  pip install -r requirements.txt
  ```

### **Environment Variables**

Create a `.env` file in the project directory and add:

```sh
GROQ_API_KEY=your_api_key_here
```

---

## **Usage**

### **1. Extract and Store Invoice Data**

- Place invoice images in the `batch_1/` folder.
- Run the script and choose whether to process images:
  ```sh
  python bill.py
  ```
- The script will:
  1. Extract text from images.
  2. Parse extracted text using **Groq LLM**.
  3. Store structured data in the SQLite database (`invoices.db`).

### **2. Query the Invoice Database**

- You can ask the AI to generate SQL queries for the stored invoices.
- Example queries:
  ```sh
  Show all unpaid invoices.
  Retrieve invoices issued by "XYZ Corp."
  Find invoices with an amount due greater than $500.
  ```
- The AI will convert your natural language query into a SQL command and execute it.

---

## **Project Structure**

```
│── batch_1/                   # Folder for invoice images
│── bill.py                     # Main script to extract, parse, and store invoices
│── database1.py                 # Database setup using SQLAlchemy
│── invoices.db                   # SQLite database storing invoices
│── .env                         # Environment variables (GROQ API key)
│── pyproject.toml                # Project configuration
│── requirements.txt              # Python dependencies
```

---

## **Database Schema**

The `invoices` table stores invoice details:

```sql
CREATE TABLE invoices (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    invoice_id TEXT UNIQUE NOT NULL,
    seller_name TEXT,
    amount_due FLOAT NOT NULL DEFAULT 0.0,
    due_date DATE,
    tax_percent FLOAT NOT NULL DEFAULT 0.0,
    status TEXT NOT NULL DEFAULT 'Unpaid'
);
```

---

## **Technology Stack**

- **Python 3.11+**
- **OpenCV & Tesseract OCR** (Text extraction)
- **LangChain + Groq LLM** (AI-powered parsing & query generation)
- **SQLAlchemy** (Database ORM)
- **SQLite** (Database storage)

---

## **License**

This project is released under the **MIT License**. See [LICENSE](LICENSE) for details.

---

## **Author**

**Sandeep Kumar**Contact: [sandeepindramohan@gmail.com](mailto\:sandeepindramohan@gmail.com)

---
