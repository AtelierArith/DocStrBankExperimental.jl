```
gsa(f, method::GSAMethod, param_range; samples, batch=false)
```

where:

  * `y=f(x)` is a function that takes in a single vector and spits out a single vector or scalar. If `batch=true`, then `f` takes in a matrix where each row is a set of parameters, and returns a matrix where each row is the output for the corresponding row of parameters.
  * `method` is one of the available GSA methods.
  * `param_range` is a vector of tuples for the upper and lower bound for the given parameter `i`.
  * `samples` is a required keyword argument for the number of samples of parameters for the design matrix. Note that this is not relevant for [Fractional Factorial Method](@ref) and [Morris Method](@ref).

Additionally,

For [Delta Moment-Independent Method](@ref), [EASI Method](@ref) and [Regression Method](@ref) input and output matrix-based method as follows is available:

```julia
res = gsa(X, Y, method)
```

where:

  * `X` is the number of parameters * samples matrix with parameter values.
  * `Y` is the output dimension * number of samples matrix with are evaluated at `X`'s columns.
  * `method` is one of the GSA methods below.

For [Sobol Method](@ref), one can use the following design matrices-based method instead of parameter range-based method discussed earlier:

```julia
effects = gsa(f, method, A, B; batch=false)
```

where `A` and `B` are design matrices, with each row being a set of parameters. Note that `generate_design_matrices` from [QuasiMonteCarlo.jl](https://docs.sciml.ai/QuasiMonteCarlo/stable/) can be used to generate the design matrices.
