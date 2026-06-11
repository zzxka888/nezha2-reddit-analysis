# Computational Analysis of Reddit Discourse on *Ne Zha 2*

This repository presents an exploratory computational study of Reddit discourse surrounding *Ne Zha 2*. It combines large-scale comment collection, text preprocessing, lexicon-based sentiment analysis, temporal trend analysis, and reply-network modeling to examine how audience reactions are expressed and propagated in online discussion.

## Research Focus

This analysis is organized around three questions:

1. What is the overall sentiment profile of Reddit discussions related to *Ne Zha 2*?
2. How does sentiment vary across time and high-engagement conversations?
3. What interaction patterns emerge when reply structure is modeled as a user network?

## Data Summary

- 100 Reddit posts collected
- 12,113 comments collected
- 10,208 comments kept after cleaning

Sentiment results on cleaned comments:

- Positive: 5,679
- Negative: 2,270
- Neutral: 2,259

The observed discussion profile is overall more positive than negative.

## Methodological Pipeline

### 1. Data Collection

Reddit data is collected with `PRAW` using the search query `"Ne Zha 2"`.

Collected fields include:

- Post ID
- Title
- Score
- URL
- Author
- Timestamp
- Number of comments
- Comment text
- Parent comment relationship

### 2. Text Preprocessing

The notebook includes:

- HTML and URL removal
- Lowercasing
- Punctuation and special-character removal
- Stopword removal
- Timestamp conversion
- Comment filtering based on score and text length

### 3. Sentiment Modeling

Sentiment is computed with **VADER**, which is well suited to short-form social media text. Comments are labeled as:

- `positive`
- `neutral`
- `negative`

### 4. Visualization and Network Analysis

The analysis includes:

- Sentiment distribution plots
- Daily sentiment trend plots
- Positive and negative word clouds
- High-upvote and high-reply comment analysis
- Reply-based user interaction graphs built with `NetworkX`

## Technical Stack

- Python
- PRAW
- pandas
- nltk
- vaderSentiment
- matplotlib
- seaborn
- WordCloud
- NetworkX
- python-louvain
- Jupyter Notebook

## Repository Structure

Suggested repository layout:

```text
.
|- notebooks/
|  |- nezha2_reddit_sentiment_network_analysis.ipynb
|- data/
|  |- raw/
|  `- processed/
|- figures/
|- .env.example
|- .gitignore
|- README.md
`- requirements.txt
```

## Reproducibility

1. Create a virtual environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Set Reddit API credentials:

```bash
export REDDIT_CLIENT_ID=your_client_id
export REDDIT_CLIENT_SECRET=your_client_secret
export REDDIT_USER_AGENT=python:movie_sentiment:v1.0
```

On Windows PowerShell:

```powershell
$env:REDDIT_CLIENT_ID="your_client_id"
$env:REDDIT_CLIENT_SECRET="your_client_secret"
$env:REDDIT_USER_AGENT="python:movie_sentiment:v1.0"
```

4. Open and run the notebook in `notebooks/`.

## Notes on Interpretation

- Do not commit real API credentials.
- If your old Reddit credentials were exposed before, rotate them before publishing.
- The current notebook is exploratory and can be further refactored into modular scripts for production-grade reproducibility.
- One merge step in the interaction-network section can inflate the intermediate dataset size, so that part of the pipeline should be interpreted carefully and may benefit from further refinement.

## Future Improvements

- Replace VADER with transformer-based sentiment models
- Refactor notebook steps into reusable Python scripts
- Improve reply-network construction logic
- Add topic modeling or keyword clustering
- Compare Reddit sentiment with other platforms
