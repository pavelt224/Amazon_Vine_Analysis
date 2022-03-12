# Amazon_Vine_Analysis

Analysis of Amazon Product Reviews (Paid Vine Program): AWS Big Data ETL with PySpark ,Python & Postgresql

## CHALLENGE OVERVIEW

The process of extracting, transforming, and loading a large dataset is demonstrated in this project. I was able to efficiently evaluate Amazon's Apparel department reviews by combining PySpark, Postgresql, and an AWS RDS server. The ETL procedure was used to see if there was any bias in favor of positive ratings from Amazon Vine users who paid for the service.

When weighing the reliability of positive evaluations on categorical items, bias determination is required. Companies pay Amazon a nominal price to deliver products to Amazon Vine members in exchange for a mandatory product review. If companies rely on product reviews to strategize future action items, it's critical to guarantee that the evaluations are truly representative of the product by distinguishing between reviews published with "marketing money" and those generated organically.

Based on a minimum count of total votes and the proportion of helpful votes relative to the total for an individual product, we will evaluate bias by repeatedly limiting our dataset to filter for only helpful evaluations. We'll compare each group's review count to the number of 5-star ratings once we've identified the paid vs. non-bought reviews.

# FEATURES AND DATA SOURCES

* Data Source: "https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Video_Games_v1_00.tsv.gz"
* Programming Files: challenge_schema.sql, Amazon_Reviews_ETL.ipynb, Vine_Review_Analysis
* Data Tools: Pandas, PySpark, Postgresql,
* Software: Google Collaboratory, Python 3.9.2, PgAdmin, AWS RDS

# CHALLENGE DELIVERABLES

* Deliverable 1: Perform ETL on Amazon Product Reviews
* Deliverable 2: Determine Bias of Vine Reviews
* Deliverable 3: A written report on the Analysis (README.md)

* Results

![Technical Analysis](https://user-images.githubusercontent.com/93852380/158035630-f090037b-0003-440e-b412-2692d8493852.png)

1- How many Vine reviews and non-Vine reviews were there?

* Total Vine reviews: 44
* Total non-Vine reviews: 8861

2- How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?

* 5-star Vine reviews: 26
* 5-star non-Vine reviews: 3233

3- What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

* % of 5-star Vine reviews: 59.09%
* % of 5-star non-Vine reviews: 37.33%


The results of the analysis show that there is no evidence of positivity bias in Vine-member evaluations. However, because this exercise lacks significant external validity—the sample size is far too tiny after severe "one size fits all" filtering, and the dataset is extremely skewed between non-vine vs vine reviews—I cannot declare with certainty that bias does not occur. Simply comparing the frequency of 5-star ratings and their penetration into the total number of helpful votes is insufficient. For example, while the percentage of 5-star vine reviews appears to be lagging by less than 10%, 24,000 5-star votes is a considerably more robust and significant datapoint than 15. We require a larger, more powerful facility. To establish a more accurate comparison of the two groups and draw bias inferences, we need a larger, more evenly distributed dataset of vine reviews, which we can get by oversampling, undersampling, or conducting ETL on a more actively shopped category.

Recommendations for Future Researchs. 

Although there is no evidence of positivity bias in Vine reviews, we need to go deeper into the dataset to conduct more studies or zoom out to our original dataset to compare our findings to the non-preprocessed and filtered data. For each star rating, for example, I'd like to see the distribution of total reviews and helpful reviews. We are currently only looking at 5-star reviews and not the rest of the reviews. To delve deeper into the data, we may generate a frequency dataframe of vine vs. non-vine reviews for each star value (1,2,3,4,5) versus the total reviews. I'd utilize this information to generate a summary statistics dataframe and plot the distribution of stars given to each group.
