```
CustomError
```

CustomError error model. Requires to definition of a variance(::CustomError, p, y) function  describing the variance of the observations and initialization function for its  parameters.

# Arguments

  * `num_params::Int`: Number of parameters to use in the error function.
  * `init_f`: Function to initialize parameters. Default = init_sigma.
