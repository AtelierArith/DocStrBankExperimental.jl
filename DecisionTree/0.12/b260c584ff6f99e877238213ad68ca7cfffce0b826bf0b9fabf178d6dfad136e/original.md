```
impurity_importance(tree; normalize::Bool = false)
impurity_importance(forest)
impurity_importance(adaboost, coeffs)
```

Return a vector of feature importance calculated by `Mean Decrease in Impurity (MDI)`.

Feature importance is computed as follows:

  * Single tree: For each feature, the associated importance is the sum, over all splits based on that feature, of the impurity decreases for that split (the node impurity minus the sum of the child impurities) divided by the total number of training observations. When `normalize` was true, the feature importances were normalized by the sum of feature importances.

More explicitly, the impurity decrease for node i is:

```
Δimpurityᵢ = nᵢ × lossᵢ - nₗ × lossₗ - nᵣ × lossᵣ
```

Where n is the number of observations, loss is entropy, gini index or other measures of impurity, index i denotes the quantity of node i, index l denotes the quantity of left child node, and index r denotes the quantity of right child node.

  * Forests: The importance for a given feature is the average over trees in the forest of the **normalized** tree importances for that feature.
  * AdaBoost models: The feature importance is as same as `split_importance`.

For forests and adaboost models, feature importance is normalized before averaging over trees, so the keyword argument `normalize` is useless. Whether to normalize or not is controversial, but the current implementation is identical to `scikitlearn`'s RandomForestClassifier, RandomForestRegressor, and AdaBoostClassifier, which is different from feature importances described in G. Louppe, “Understanding Random Forests: From Theory to Practice”, PhD Thesis, U. of Liege, 2014. (https://arxiv.org/abs/1407.7502). See this [PR](https://github.com/scikit-learn/scikit-learn/issues/19972) for a detailed discussion.

If `impurity_importance` was set false when building the tree, this function returns an empty vector.

Warn:     The importance might be misleading because MDI is a biased method.     See [Beware Default Random Forest Importances](https://explained.ai/rf-importance/index.html) for more discussion.
