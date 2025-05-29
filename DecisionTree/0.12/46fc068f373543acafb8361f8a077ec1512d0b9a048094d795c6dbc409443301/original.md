```
apply_adaboost_stumps_proba(stumps::Ensemble, coeffs, features, labels::AbstractVector)
```

Compute $P(L=label|X)$ for each row in `features`, returning a `N_row` x `n_labels` matrix of probabilities, each row summing to one.

`col_labels` is a vector containing the distinct labels, eg. `["versicolor", "virginica", "setosa"]`. Its ordering determines the column ordering of the output matrix.

See also [`build_adaboost_stumps`](@ref). 
