```
apply_tree_proba(tree, features, col_labels::AbstractVector)
```

For the specified `tree`, compute $P(L=label|X)$ for each row in `features`, returning an `N_row` x `n_labels` matrix of probabilities, each row summing to one. Here `tree` is any `DecisionTree.Root`, `DecisionTree.Node` or `DecisionTree.Leaf` instance, as returned, for example, by [`build_tree`](@ref).

`col_labels` is a vector containing the distinct labels, eg. `["versicolor", "virginica", "setosa"]`. It's order determines the column ordering of the output matrix.

See also [`build_tree`](@ref).
