# DSI project 3: Using NLP to Predict if a News Article is from The Onion

_Submitted: February 1st, 2020_

### Executive Summary

The Onion is an American newspaper and digital media company that publishes satirical articles about international, national, and local news. They frequently provide hilarious fake news stories with characteristic sarcastic, crass headlines accompanied by an article or sometimes video. Many people sometimes are shocked by headlines, only to discover that they're from The Onion. At the same time, however, many people are unaware that The Onion is entirely satire and may even mistake their articles for the truth. 

While The Onion posts are lighthearted and harmless humor to those who know they are fake stories, some people are still being fooled into thinking that they are true stories. At the same, fake news is an ever persistent and growing issue with many parallels that can be drawn to stories from The Onion.  

This report seeks to develop and refine a tool that is capable of reading a reddit post and predicting whether it came from The Onion subreddit, or from one of five other legitimate news posting subreddits. The tool uses Natural Language Processing (NLP) models to learn patterns in the language of posts from The Onion and then determine whether a post from an unknown origin came from The Onion or not. While this tool cannot predict fake news from all platforms, it serves as a starting point to establish proof of concept that a computer is able to judge whether or not a news story is sarcastic or satirical. The hope is to improve and scale this sort of tool up into a search engine filter that would be able to block news articles that it knows are fake from appearing in search results, and then give a rating of suspected probability for stranger articles that it believes are fake. 

---

### Primary findings

Data were gathered from 6 different subreddits using Reddit's API push.io. 1000 posts were scrapped from the r/TheOnion subreddit and 1000 more were taken each from: r/nottheonion, r/news, r/usnews, r/worldnews, and r/breitbart. All of these subreddits are characterized by a single explanatory news headline in the title. The post text usually contains a link to the corresponding story, and people rarely comment on these posts. That is why only the title was used as input into the models. 

The data were divided into two different sets to be modeled from. Dataset 1 consisted of 1000 r/TheOnion posts and 1000 r/nottheonion posts. Dataset 2 consisted of 1000 r/TheOnion posts along with 300 posts randomly selected from each of the five other subreddits previously mentioned. The second dataset was meant to give an accurate portrayal of real life news headlines in order to test the model's ability to adapt to new articles. 

All posts were transformed using the Term Frequency inverse Document Frequency vectorizer (TFIDF), producing a matrix of over 5000 relevant words taken into account in each model due to their high frequency. Next, five different models were fit to the training data and then evaluated by their accuracy. The models included: logistic regression (lr), decision tree, multinomial naive bayes (mnb), gaussian naive bayes, and random forest classification. 

---

### Conclusions and Next Steps

Lr and mnb models had the highest accuracy scores across both datasets and were examined more closely in further evaluation. Lr achieved scores of 0.812 and 0.755 for datasets 1 and 2 respectively while mnb achieved scores of 0.814 and 0.781. Feature importance can be inferred from the lr coefficient values. The words: this, of, onion, just and nation were in the top 8 most highly correlated features to the r/TheOnion page for both datasets. On the other hand, the words: Kobe Bryant, coronavirus, police, man, bank, and charged were amongst the list of words most negatively correlated with r/TheOnion. 

These results show that it is in fact possible to predict whether or not a news article is from The Onion using NLP with an accuracy greater than the baseline. Accuracy did decrease, however, between datasets 1 and 2. In order to improve, more data must be gathered, and the inclusion of the full article in the model fitting will likely improve accuracy even more. Other next steps for improvement would be to use more computationally intensive models like boosting or neural networks. 
