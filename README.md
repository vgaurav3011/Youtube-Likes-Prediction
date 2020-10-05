# Youtube-Likes-Prediction

**What Worked and What Did Not?**

- One Hot Encoding on the categorical columns set did work only till minimizing the error to 650 with XGBRegressor and CatBoostRegressor, hence did not work well.
-  Label Encoding on Categorical Columns proved to be a better idea, since the number of category ids were less than 30, and further we can use their label encoded values to create aggregation based features.
- The numerical columns are highly correlated to the target variable, hence it performs decently well alone too, but aggregated features from them would be more beneficial.
- Using transformed min,max,sum,mean features with group by using the label encoded and the numerical columns proved to be more useful than numerical columns alone.
- Using country code as the group by aggregation proved to be useful.
- Textual features were handled by taking account of their lengths, with len(description) proving to be highly valuable.
- Aggregated features created from description are useful, however the title aggregated features did not work well (as we observed longer the title, the lesser number of likes on the video).
- We make use of top N words using count vectorizer on the description and tags, that worked well.
- Additionally, (not tried) but we can make use of counting the number of tags, with each video, by stripping the limiter '|' and higher number of tags correlates to lesser number of views.
- Also, we can also use VADER polarity scores on the description to gain whether negative or positive video descriptions works well.
- CatBBoost and XGB Regressor does not converge well.
- We determined the optimal threshold for LGBM to be 0.99 which practically boiled down to the idea that stacked ensembles do not work well.
- Better hyperparameter tuning of the LGBM would have yielded better results, with the current model ranking at Public Leaderboard Rank 10.
