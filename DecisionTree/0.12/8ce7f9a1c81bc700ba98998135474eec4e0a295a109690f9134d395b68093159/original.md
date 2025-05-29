```
prune_tree(tree::Union{Root, LeafOrNode}, purity_thresh=1.0, loss::Function)
```

Prune `tree` based on prediction accuracy of each node. Here `tree` is any `DecisionTree.Root`, `DecisionTree.Node` or `DecisionTree.Leaf` instance, as returned, for example, by [`build_tree`](@ref).

  * `purity_thresh`: If the prediction accuracy of a stump is larger than this value, the node will be pruned and become a leaf.
  * `loss`: The loss function for computing node impurity. Available function include `DecisionTree.util.entropy`, `DecisionTree.util.gini` and `DecisionTree.mean_squared_error`. Defaults are `entropy` and `mean_squared_error` for classification tree and regression tree, respectively. If the tree is not a `Root`, this argument does not affect the result.

For a tree of type `Root`, when any of its nodes are pruned, the `featim` field will be updated by recomputing the impurity decrease of that node divided by the total number of training observations and subtracting the value.  The computation of impurity decrease is based on node impurity calculated with the loss function provided as the argument `loss`. The algorithm is as same as that described in the [`impurity_importance`](@ref) documentation.

This function will recurse until no stumps can be pruned.

!!! warning
    For regression trees, pruning trees based on accuracy may not be an appropriate method.


See also [`build_tree`](@ref).
