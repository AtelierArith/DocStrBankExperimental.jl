```
choice_optimize(model, options)
```

Optimize choice-related model parameters for a `neural_choiceDDM` using choice data.

Arguments: 

  * `model`: an instance of a `neural_choiceDDM`.

Returns:

  * `model`: an instance of a `neural_choiceDDM`.
  * `output`: results from [`Optim.optimize`](@ref).
