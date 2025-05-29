```
function GaussianEmission(; output_dim::Int, μ::Vector{<:Real}=zeros(output_dim), Σ::Matrix{<:Real}=Matrix{Float64}(I, output_dim, output_dim))
```

Functon to create a GaussianEmission with given output dimension, mean, and covariance.

# Arguments

  * `output_dim::Int`: The output dimension of the emission
  * `μ::Vector{<:Real}=zeros(output_dim)`: The mean of the Gaussian
  * `Σ::Matrix{<:Real}=Matrix{Float64}(I, output_dim, output_dim))`: The covariance matrix of the Gaussian

# Returns
