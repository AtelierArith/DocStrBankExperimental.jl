```
informationmatrix(model::BetaRegressionModel; expected=true)
```

Compute the information matrix of the model. By default, this is the Fisher information, i.e. the expected value of the matrix of second partial derivatives of [`loglikelihood`](@ref) with respect to each element of [`params`](@ref). Set `expected` to `false` to obtain the observed information.

See also: [`vcov`](@ref), [`score`](@ref)
