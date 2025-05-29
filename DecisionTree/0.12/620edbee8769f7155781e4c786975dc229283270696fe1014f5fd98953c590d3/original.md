```
apply_forest_proba(forest::Ensemble, features, col_labels::AbstractVector)
```

For the specified `forest`, compute $P(L=label|X)$ for each row in `features`, returning a `N_row` x `n_labels` matrix of probabilities, each row summing to one. Here `forest` is any `DecisionTree.Ensemble` instance, as returned, for example, by [`build_forest`](@ref).

`col_labels` is a vector containing the distinct labels, eg. `["versicolor", "virginica", "setosa"]`. It's order determines the column ordering of the output matrix.

See also [`build_forest`](@ref).
