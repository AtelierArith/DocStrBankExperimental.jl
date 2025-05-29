```
score(model::BetaRegressionModel)
```

Compute the score vector of the model, i.e. the vector of first partial derivatives of [`loglikelihood`](@ref) with respect to each element of [`params`](@ref).

See also: [`informationmatrix`](@ref)
