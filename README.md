# The impact of Standardization in classification algorithms accuracy

## Context

It is common in Machine Learning to standardize your data before training. This work compares the results of standardized vs non-standardized data in 6 popular classification algorithms.

## Datasets

[Pima Indians Diabetes Database](https://www.kaggle.com/uciml/pima-indians-diabetes-database/data) 

[banknote authentication Data Set](http://archive.ics.uci.edu/ml/datasets/banknote+authentication)

[Breast Cancer Wisconsin (Diagnostic) Data Set](https://www.kaggle.com/uciml/breast-cancer-wisconsin-data)

I **did not** make any treatment in the data beforehand. The data was used as it was available from the repositories. When applicable, only the `ID` columns were removed. 

The standardization was performed using sklearn's [StandardScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html), which according to the documentation:

>Standardize features by removing the mean and scaling to unit variance
>
>The standard score of a sample x is calculated as:
>
>    z = (x - u) / s
>
>where u is the mean of the training samples or zero if with_mean=False, and s is the standard deviation of the training samples or one if with_std=False.

## Results

The difference was calculated based on the not standardized results.

### Logistic Regression

| Standardized | Cancer| Banknote | Diabetes |
|---|---|---|---|
| Not  | 0.9561  | 0.9855  | 0.7597 |
| Yes  | 0.9737  | 0.9782  | 0.7532 |
| Diff | +1.84%  | -0.74%  | -0.86% | 

### K Nearest Neighbors (KNN)

| Standardized | Cancer| Banknote | Diabetes |
|---|---|---|---|
| Not  | 0.9561 | 1.0000 | 0.6623 |
| Yes  | 0.9474 | 1.0000 | 0.6883 |
| Diff | -0.91% | +/-0%  | +3.93% |

### Decision Tree

| Standardized | Cancer| Banknote | Diabetes |
|---|---|---|---|
| Not  | 0.9474 | 0.9782 | 0.7273 |
| Yes  | 0.9298 | 0.9818 | 0.7468 |
| Diff | -1.86% | +0.37% | +2.68% |

### Support Vector Machine (SVC)

| Standardized | Cancer| Banknote | Diabetes |
|---|---|---|---|
| Not  | 0.6228 | 1.0000 | 0.6429 |
| Yes  | 0.9737 | 1.0000 | 0.7338 |
| Diff | +56.3% | +/-0%  | +14.1% |

### Gradient Boosting

| Standardized | Cancer| Banknote | Diabetes |
|---|---|---|---|
| Not  | 0.9561 | 1.0000 | 0.7403 |
| Yes  | 0.9561 | 1.0000 | 0.7403 |
| Diff | +/-0%  | +/-0%  | +/-0%  |

### Random Forest

| Standardized | Cancer| Banknote | Diabetes |
|---|---|---|---|
| Not  | 0.9649 | 0.9927 | 0.7273 |
| Yes  | 0.9649 | 0.9927 | 0.7273 |
| Diff | +/-0%  | +/-0%  | +/-0%  |

## Result Analysis

Except for the Support Vector Machine, standardization did not provide a huge advantage in the selected algorithms and datasets. The Diabetes dataset (which is the largest of the three) was the one that benefited the most from the standardized values. This might be an indication that more complex datasets may benefit more from standardization.

Also, some algorithms are not expected to have performance gains with standardized data. This is the case of decision trees for example.

## Conclusion

Standardization by itself did not provide huge benefits in most classification algorithms in the selected datasets. However, the fact that those datasets are small and well behaved might have a part in the results.

Standardization is still recommended because it can benefit the convergence speed. 

## Future works

I would like to revisit this theme in the future with larger datasets to get more conclusive results. Also, I would like to compare the convergence speed of standardized and non-standardized data.