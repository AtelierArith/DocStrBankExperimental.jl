```
AdaBoostStumpClassifier(; n_iterations::Int=10,
                        rng=Random.GLOBAL_RNG)
```

Adaboosted decision tree stumps. See [DecisionTree.jl's documentation](https://github.com/bensadeghi/DecisionTree.jl)

Hyperparameters:

  * `n_iterations`: number of iterations of AdaBoost
  * `rng`: the random number generator to use. Can be an `Int`, which will be used to seed and create a new random number generator.

Implements `fit!`, `predict`, `predict_proba`, `get_classes`
