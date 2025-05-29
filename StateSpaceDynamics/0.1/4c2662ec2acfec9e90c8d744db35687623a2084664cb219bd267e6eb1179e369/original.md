```
PoissonRegressionEmission
```

A Poisson regression model.

# Fields

  * `input_dim::Int`: Dimension of the input data.
  * `include_intercept::Bool = true`: Whether to include an intercept term.
  * `β::Vector{<:Real} = if include_intercept zeros(input_dim + 1) else zeros(input_dim) end`: Coefficients of the model. The first element is the intercept term, if included.
  * `λ::Float64 = 0.0`: Regularization parameter.
