```
RandomForest(
  Dict(
    :output => :class,
    :num_subfeatures => 0,
    :num_trees => 10,
    :partial_sampling => 0.7,
    :max_depth => -1
  )
)
```

Random forest classification.  See [DecisionTree.jl's documentation](https://github.com/bensadeghi/DecisionTree.jl)

Hyperparmeters:

  * `:num_subfeatures` => 0  (number of features to consider at random per split)
  * `:num_trees` => 10 (number of trees to train)
  * `:partial_sampling` => 0.7 (fraction of samples to train each tree on)
  * `:max_depth` => -1 (maximum depth of the decision trees)
  * `:min_samples_leaf` => 1 (the minimum number of samples each leaf needs to have)
  * `:min_samples_split` => 2 (the minimum number of samples in needed for a split)
  * `:min_purity_increase` => 0.0 (minimum purity needed for a split)

Implements `fit!`, `transform!`
