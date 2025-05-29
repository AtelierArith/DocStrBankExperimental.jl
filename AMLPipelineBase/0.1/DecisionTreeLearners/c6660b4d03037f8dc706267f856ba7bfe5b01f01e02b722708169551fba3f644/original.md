```
Adaboost(
  Dict(
    :output => :class,
    :num_iterations => 7
  )
)
```

Adaboosted decision tree stumps. See [DecisionTree.jl's documentation](https://github.com/bensadeghi/DecisionTree.jl)

Hyperparameters:

  * `:num_iterations` => 7 (number of iterations of AdaBoost)

Implements `fit!`, `transform!`
