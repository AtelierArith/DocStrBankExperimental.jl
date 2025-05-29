```
choice_neural_optimize(model, options)
```

Optimize (potentially all) model parameters for a `neural_choiceDDM` using choice and neural data.

Arguments: 

  * `model`: an instance of a `neural_choiceDDM`.

Returns:

  * `model`: an instance of a `neural_choiceDDM`.
  * `output`: results from [`Optim.optimize`](@ref).
