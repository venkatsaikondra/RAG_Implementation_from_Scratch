# 🔍 RAG From Scratch

A minimal, dependency-light implementation of **Retrieval-Augmented Generation (RAG)** built from the ground up using pure Python — no vector databases, no heavyweight frameworks, just math and logic.

---

## 📌 Overview

This project demonstrates how RAG works under the hood by implementing the retrieval component manually using **cosine similarity** on raw token counts. Given a user query, the system finds the most semantically relevant document from a corpus and returns it.

---

## 🧠 How It Works

```
User Query ──► Tokenize ──► Count Vectors ──► Cosine Similarity ──► Best Match
                                                      ▲
                                               Corpus Documents
```

### Key Steps

1. **Tokenization** — Split query and each document into lowercase word tokens
2. **Term Frequency Counting** — Use `Counter` to build bag-of-words vectors
3. **Cosine Similarity** — Measure the angle between query and document vectors
4. **Retrieval** — Return the document with the highest similarity score

### Cosine Similarity Formula

$$\text{similarity} = \frac{\vec{q} \cdot \vec{d}}{|\vec{q}| \times |\vec{d}|}$$

Where:
- $\vec{q}$ = query term frequency vector
- $\vec{d}$ = document term frequency vector

---

## 📁 Project Structure

```
rag_from_scratch/
│
├── rag.py               # Core cosine similarity & retrieval logic
├── corpus.py            # Sample document corpus
├── README.md            # You are here
└── notebook.ipynb       # Step-by-step walkthrough (optional)
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.7+
- No external libraries required! (only Python standard library)

### Installation

```bash
git clone https://github.com/your-username/rag_from_scratch.git
cd rag_from_scratch
```

### Usage

```python
from rag import return_response

corpus_of_documents = [
    "Take a leisurely walk in the park and enjoy the fresh air.",
    "Visit a local museum and discover something new.",
    "Attend a live music concert and feel the rhythm.",
    "Go for a hike and admire the natural scenery.",
    "Have a picnic with friends and share some laughs.",
    "Explore a new cuisine by dining at an ethnic restaurant.",
    "Take a yoga class and stretch your body and mind.",
    "Join a local sports league and enjoy some friendly competition.",
    "Attend a workshop or lecture on a topic you're interested in.",
    "Visit an amusement park and ride the roller coasters."
]

query = "i like fresh air"
response = return_response(query, corpus_of_documents)
print(response)
# Output: 'Take a leisurely walk in the park and enjoy the fresh air.'
```

---

## 🔬 Core Functions

### `cosine_similarity2(query, document)`

Computes the cosine similarity between a query string and a document string.

| Parameter  | Type  | Description                    |
|------------|-------|--------------------------------|
| `query`    | `str` | The user's input query         |
| `document` | `str` | A single document from corpus  |

**Returns:** `float` — similarity score between `0.0` and `1.0`

---

### `return_response(query, corpus)`

Finds and returns the most relevant document from the corpus for a given query.

| Parameter | Type        | Description                          |
|-----------|-------------|--------------------------------------|
| `query`   | `str`       | The user's input query               |
| `corpus`  | `list[str]` | List of candidate documents          |

**Returns:** `str` — the most relevant document

---

## 📊 Example Queries

| Query | Returned Document |
|---|---|
| `"i like fresh air"` | *Take a leisurely walk in the park and enjoy the fresh air.* |
| `"i like to do yoga"` | *Take a yoga class and stretch your body and mind.* |
| `"i want to eat something new"` | *Explore a new cuisine by dining at an ethnic restaurant.* |

---

## ⚙️ Limitations

- **No stemming/lemmatization** — "run" and "running" are treated as different tokens
- **No IDF weighting** — common words like "the", "and" are not down-weighted
- **Exact token matching only** — synonyms and semantically similar words are not matched
- **Not suitable for large corpora** — scales as O(n × m) with corpus and document size

---

## 🛣️ Roadmap / Improvements

- [ ] Add stopword removal
- [ ] Implement TF-IDF weighting
- [ ] Add BM25 ranking
- [ ] Integrate sentence-transformers for dense embeddings
- [ ] Add FAISS for scalable vector search
- [ ] Connect to an LLM to generate answers from retrieved context

---

## 🧩 Concepts Covered

- Bag-of-Words (BoW) representation
- Term Frequency (TF) vectors
- Cosine similarity for text matching
- Retrieval pipeline design
- Foundation for understanding tools like LangChain, LlamaIndex, etc.

---

## 📚 Further Reading

- [Cosine Similarity — Wikipedia](https://en.wikipedia.org/wiki/Cosine_similarity)
- [Retrieval-Augmented Generation (RAG) — Lewis et al., 2020](https://arxiv.org/abs/2005.11401)
- [TF-IDF Explained](https://en.wikipedia.org/wiki/Tf%E2%80%93idf)

---

## 🪪 License

MIT License — feel free to use, modify, and distribute.

---

## 🙋 Author

Built with curiosity and plain Python. Contributions welcome!
