```
split_importance(tree; normalize::Bool = false)
split_importance(forest)
split_importance(adaboost, coeffs)
```

Return a vector of feature importance based on the number of times a feature was used in a split.

Feature importance is computed as follows:

  * Single tree: For each feature, the associated importance is the number of splits based on that feature.
  * Forests: The importance for a given feature is the average over trees in the forest of the **normalized** tree importances for that feature.
  * AdaBoost models: The importance of each feature is the mean number of splits based on that feature across each stump, weighted by estimator weights (`coeffs`).

For forests and adaboost models, feature importance is normalized before averaging over trees, so keyword argument `normalize` is useless.
