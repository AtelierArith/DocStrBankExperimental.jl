```
fit(model, options)
```

fit model parameters for a `noiseless_neuralDDM`.

Arguments: 

  * `model`: an instance of a `noiseless_neuralDDM`.
  * `options`: some details related to the optimzation, such as which parameters were fit (`fit`), and the upper (`ub`) and lower (`lb`) bounds of those parameters.

Returns:

  * `model`: an instance of a `noiseless_neuralDDM`.
  * `output`: results from [`Optim.optimize`](@ref).
