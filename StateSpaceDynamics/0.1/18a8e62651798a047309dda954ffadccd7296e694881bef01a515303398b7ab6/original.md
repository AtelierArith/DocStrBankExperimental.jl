```
fit!(model::GaussianEmission, Y::Matrix{<:Real}, w::Vector{Float64}=ones(size(Y, 1)))
```

Fit a GaussianEmission model to the data `Y`. 

# Arguments

  * `model::GaussianEmission`: Gaussian model to fit.
  * `Y::Matrix{<:Real}`: Data to fit the model to. Should be a matrix of size `(n, output_dim)`.
  * `w::Vector{Float64}=ones(size(Y, 1))`: Weights for the data. Should be a vector of size `n`.
