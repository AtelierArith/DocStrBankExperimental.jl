```
struct TEModel
```

Universal datatype for storing information about a Tree Ensemble Model. This is the datatype that is used when creating the integer optimization problem from a tree ensemble.

Different tree models (EvoTrees, XGBoost, RandomForest) require individual conversion functions to this datatype.

# Fields

  * `n_trees`: number of trees in the ensemble
  * `n_feats`: number of features (input variables) in the model
  * `n_leaves`: number of leaves on each tree
  * `leaves`: indices of the leaves on each tree
  * `splits`: [feature, splitpoint index] pairs accessible by [tree, node]
  * `splits_ordered`: splitpoints ordered by split value for each feature
  * `n_splits`: number of splitpoints for each feature
  * `predictions`: prediction of each node (zero for nodes that are not leaves)
  * `split_nodes`: boolean array containing information whether a node is a split node or not

Splitpoints is the set of unique condition values from the ensemble. Each node is associated with a condition value.
