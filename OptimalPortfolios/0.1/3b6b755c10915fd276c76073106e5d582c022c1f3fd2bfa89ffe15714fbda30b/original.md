```
allocate(X, lower, upper; rf = 0.0, denoise = false, fullinvest = true,
```

method = "MSR")

Compute optimal % allocations according to given method.

# Arguments

  * `X::Matrix{Float64}`: N x T returns matrix, where N is the number of assets and T is the number of samples.
  * `lower::Union{Float64, Vector{Float64}}`: lower bound on allocations in %; if specified as a scalar, then the same value is applied to all assets.
  * `upper::Union{Float64, Vector{Float64}}`: upper bound on allocations in %; if specified as a scalar, then the same value is applied to all assets.
  * `rf::Float64=0.0`: risk-free rate; applicable only for MSR method.
  * `denoise::Bool=False`: If true, sample covariance matrix will be de-noised by flooring the eigen values at λmax estimated from Marcenko-Pastur distribution.
  * `fullinvest::Bool=True`: If true, allocations will sum to 1.

Returns a vector of % allocations.
