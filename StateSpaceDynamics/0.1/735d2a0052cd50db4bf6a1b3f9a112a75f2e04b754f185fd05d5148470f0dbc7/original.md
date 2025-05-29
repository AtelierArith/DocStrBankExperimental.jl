```
GaussianRegressionEmission
```

A Gaussian regression Emission model.

# Fields

  * `input_dim::Int`: Dimension of the input data.
  * `output_dim::Int`: Dimension of the output data.
  * `include_intercept::Bool = true`: Whether to include an intercept term; if true, the first column of β is assumed to be the intercept/bias.
  * `β::Matrix{<:Real} = if include_intercept zeros(input_dim + 1, output_dim) else zeros(input_dim, output_dim) end`: Coefficient matrix of the model. Shape input*dim by output*dim. The first row are the intercept terms, if included.
  * `Σ::Matrix{<:Real} = Matrix{Float64}(I, output_dim, output_dim)`: Covariance matrix of the model.
  * `λ::Float64 = 0.0`: Regularization parameter.
