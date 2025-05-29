```
PrunedTree(
  Dict(
    :purity_threshold => 1.0,
    :max_depth => -1,
    :min_samples_leaf => 1,
    :min_samples_split => 2,
    :min_purity_increase => 0.0
  )
)
```

Decision tree classifier.   See [DecisionTree.jl's documentation](https://github.com/bensadeghi/DecisionTree.jl)

Hyperparmeters:

  * `:purity_threshold` => 1.0 (merge leaves having >=thresh combined purity)
  * `:max_depth` => -1 (maximum depth of the decision tree)
  * `:min_samples_leaf` => 1 (the minimum number of samples each leaf needs to have)
  * `:min_samples_split` => 2 (the minimum number of samples in needed for a split)
  * `:min_purity_increase` => 0.0 (minimum purity needed for a split)

Implements `fit!`, `transform!`
