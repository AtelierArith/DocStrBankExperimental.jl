```
DecisionTreeClassifier(; pruning_purity_threshold=0.0,
                       max_depth::Int=-1,
                       min_samples_leaf::Int=1,
                       min_samples_split::Int=2,
                       min_purity_increase::Float=0.0,
                       n_subfeatures::Int=0,
                       rng=Random.GLOBAL_RNG,
                       impurity_importance::Bool=true)
```

Decision tree classifier. See [DecisionTree.jl's documentation](https://github.com/bensadeghi/DecisionTree.jl)

Hyperparameters:

  * `pruning_purity_threshold`: (post-pruning) merge leaves having `>=thresh` combined purity (default: no pruning)
  * `max_depth`: maximum depth of the decision tree (default: no maximum)
  * `min_samples_leaf`: the minimum number of samples each leaf needs to have (default: 1)
  * `min_samples_split`: the minimum number of samples in needed for a split (default: 2)
  * `min_purity_increase`: minimum purity needed for a split (default: 0.0)
  * `n_subfeatures`: number of features to select at random (default: keep all)
  * `rng`: the random number generator to use. Can be an `Int`, which will be used to seed and create a new random number generator.
  * `impurity_importance`: whether to calculate feature importances using `Mean Decrease in Impurity (MDI)`. See [`DecisionTree.impurity_importance`](@ref)

Implements `fit!`, `predict`, `predict_proba`, `get_classes`
