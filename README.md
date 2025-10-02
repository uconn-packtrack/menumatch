# MenuMatch 🍽️

**UConn Dining Hall Meal Recognition & Nutrition Estimation**

MenuMatch is a containerized service that takes in a food photo along with context (dining hall, date, time) and outputs:

* ✅ Identified menu items on the plate
* ✅ Estimated portion sizes / servings
* ✅ Nutritional information per item and in total

It is designed to integrate with the **HuskyEats** student app, but can also be run as a standalone API.

---

## ⚙️ How It Works

1. **Input**: Image of a meal + context (`location`, `date`, `time`)
2. **Model**: AI / rule-based algorithm matches food against menu data
3. **Output**: JSON with food items, serving size estimates, and nutrition

---

## 🛠 Tech Stack

* **Containerization**: Docker
* **Backend**: Python (FastAPI/Flask)
* **ML / AI**: CLIP-based embeddings, rule-based heuristics for portions
* **Data**: Daily-scraped UConn Dining menus + nutrition info
* **Integration**: REST API (for HuskyEats app or standalone use)

---

## 🚀 Quick Start

```bash
git clone https://github.com/<org>/menumatch.git
cd menumatch
docker build -t menumatch .
docker run -p 5000:5000 menumatch
```

Example request:

```bash
curl -X POST -F "image=@meal.jpg" \
     -F "location=Putnam" \
     -F "date=2025-02-01" \
     -F "time=lunch" \
     http://localhost:5000/analyze
```

Example response:

```json
{
  "items": [
    { "name": "Grilled Chicken", "serving_size": "4 oz", "calories": 220 },
    { "name": "Brown Rice", "serving_size": "1 cup", "calories": 215 }
  ],
  "total_nutrition": { "calories": 435 }
}
```

---

## 🔮 Roadmap

* Improve portion estimation accuracy
* Support multiple images / angles
* Integrate directly into HuskyEats app
