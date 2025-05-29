```
RandomForestRegressor(; n_subfeatures::Int=-1,
                      n_trees::Int=10,
                      partial_sampling::Float=0.7,
                      max_depth::Int=-1,
                      min_samples_leaf::Int=5,
                      rng=Random.GLOBAL_RNG,
                      impurity_importance::Bool=true)
```

Random forest regression. See [DecisionTree.jl's documentation](https://github.com/bensadeghi/DecisionTree.jl)

Hyperparameters:

  * `n_subfeatures`: number of features to consider at random per split (default: -1, sqrt(# features))
  * `n_trees`: number of trees to train (default: 10)
  * `partial_sampling`: fraction of samples to train each tree on (default: 0.7)
  * `max_depth`: maximum depth of the decision trees (default: no maximum)
  * `min_samples_leaf`: the minimum number of samples each leaf needs to have (default: 5)
  * `min_samples_split`: the minimum number of samples in needed for a split
  * `min_purity_increase`: minimum purity needed for a split
  * `rng`: the random number generator to use. Can be an `Int`, which will be used to seed and create a new random number generator. Multi-threaded forests must be seeded with an `Int`
  * `impurity_importance`: whether to calculate feature importances using `Mean Decrease in Impurity (MDI)`. See [`DecisionTree.impurity_importance`](@ref).

Implements `fit!`, `predict`, `get_classes`
