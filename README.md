# Entity-Level Twitter Sentiment Analysis with PySpark

## Project Overview

This project builds a scalable natural language processing pipeline for entity-level Twitter sentiment analysis. PySpark is used for distributed data loading, cleaning, transformation and aggregation, while VADER is used to classify tweets as positive, negative or neutral.

The project was completed as part of the PGC7223 Big Data Analysis course and demonstrates practical skills in big data processing, NLP, visualization and critical model evaluation.

## Dataset

The project uses the validation split of the [Twitter Entity Sentiment Analysis dataset](https://www.kaggle.com/datasets/jp797498e/twitter-entity-sentiment-analysis).

The original dataset contains:

* 1,000 labelled tweets
* 32 entities, including gaming and technology brands
* Four original labels: Positive, Negative, Neutral and Irrelevant
* Four fields: TweetID, Entity, Sentiment and Tweet content

After removing one duplicated tweet, 999 records were retained for analysis. Because VADER predicts only positive, negative and neutral sentiment, the original Irrelevant label was merged into Neutral for three-class evaluation.

## Tools and Technologies

* Python
* PySpark and Spark SQL
* PySpark MLlib
* NLTK
* VADER Sentiment Analyzer
* Pandas
* Matplotlib
* Seaborn
* WordCloud
* Google Colab

## Analysis Workflow

1. Load the UTF-8 CSV dataset with PySpark.
2. Inspect the schema, missing values and duplicate records.
3. Normalize text by converting it to lowercase and removing unnecessary characters.
4. Tokenize the text and remove English stop words.
5. Apply lemmatization using an NLTK user-defined function.
6. Calculate VADER compound sentiment scores from the original tweet text.
7. Classify each tweet as positive, negative or neutral.
8. Evaluate predictions against the dataset labels.
9. Visualize sentiment distribution, frequent terms and hashtags.

## Results

The VADER model achieved an overall accuracy of **40.94%**.

| Sentiment | Precision | Recall | F1-score |
| --------- | --------: | -----: | -------: |
| Positive  |    40.48% | 73.19% |   52.13% |
| Negative  |    40.60% | 60.90% |   48.72% |
| Neutral   |    44.55% |  9.85% |   16.13% |

The results show that VADER identified many positive and negative tweets but performed poorly on neutral content. This indicates that a general-purpose lexicon-based model has difficulty distinguishing neutral and entity-irrelevant language in domain-specific social media data.

## Key Learning Outcomes

Through this project, I developed practical skills in:

* Distributed text processing with PySpark
* NLP preprocessing and sentiment analysis
* Spark DataFrame transformations and UDFs
* Model evaluation using precision, recall, F1-score and accuracy
* Data visualization and analytical communication
* Identifying the limitations of general-purpose NLP models

## Limitations and Future Work

VADER is transparent and computationally efficient, but it does not fully capture sarcasm, gaming terminology, contextual meaning or entity relevance. Future work could compare VADER with machine-learning and transformer-based models such as logistic regression, BERT or Spark NLP classifiers.

## Repository Contents

* `pyspark_entity_sentiment_analysis.ipynb` — complete analysis notebook
* `twitter_validation.csv` — validation dataset used in the project

## How to Run

1. Open the notebook in Google Colab.
2. Upload `twitter_validation.csv` to the Colab session.
3. Run all notebook cells in order.
4. Review the generated evaluation metrics and visualizations.
