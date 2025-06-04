# 🕸️ Web Scraping with Python - Practical Projects

This repository contains multiple examples and detailed explanations on how to perform **web scraping** using Python. Web scraping is one of the most essential skills in Data Science when APIs are not available.

---

## 🧠 What is Web Scraping?

Web scraping is the process of **automatically extracting data** from websites. This data can be anything such as product details, job listings, news articles, etc.

---

## 📍 Why Use Web Scraping?

- Website doesn’t offer an API.
- You want to analyze public data from a web page.
- Automate data collection instead of doing it manually.
- Get fresh, real-time data for analysis.

---

## 🧰 Tools Used

| Tool | Use |
|------|-----|
| `requests` | To send HTTP requests and download web pages |
| `BeautifulSoup` | To parse HTML content and extract needed parts |
| `pandas` | To organize and save the extracted data |
| `lxml` | Fast HTML/XML parser (used by BeautifulSoup) |
| `Selenium` | (Optional) for dynamic JavaScript content |
| `time` | To add delays between requests (avoid blocking) |
| `csv` | To export data manually if needed |

Install them with:

```bash
pip install requests beautifulsoup4 pandas lxml
```

---

## 📁 Project Examples

### 1️⃣ Scrape Laptop Data from Jumia Egypt

Extract product titles and prices.

```python
import requests
from bs4 import BeautifulSoup
import pandas as pd

url = "https://www.jumia.com.eg/laptops/"
headers = {"User-Agent": "Mozilla/5.0"}

response = requests.get(url, headers=headers)
soup = BeautifulSoup(response.content, "html.parser")
products = soup.find_all("article", class_="prd")

data = []
for product in products:
    try:
        title = product.find("h3").text.strip()
        price = product.find("div", class_="prc").text.strip()
        data.append({"Title": title, "Price": price})
    except:
        continue

df = pd.DataFrame(data)
df.to_csv("jumia_laptops.csv", index=False)
print("Saved to CSV ✅")
```

### 2️⃣ Scrape Job Listings from Wuzzuf

Coming soon: Scrape job titles, companies, and locations.

---

## 💡 Tips for Scraping

- Always check `robots.txt` (e.g., `https://www.jumia.com.eg/robots.txt`) to see if scraping is allowed.
- Add delays between requests using `time.sleep(2)` to avoid being blocked.
- Don't send many requests per second — websites may block your IP.
- Use headers to mimic a real browser (User-Agent).

---



---

## 📜 License

This project is open-source and free to use. Always give credit if you use the code.

---

## 📬 Contact

- **Email**: omarramadan88888888g@gmail.com
- **GitHub**: [YourProfile](https://github.com/omarrama555)
