```
sampleK(params::PriorHyperparamsList, numsamples::Int, n::Int)::Vector{Int}
sampleK(η::Real, σ::Real, u::Real, v::Real, numsamples::Int, n::Int)
```

Returns a vector of length `numsamples` containing samples of $K$ (number of clusters) generated from its marginal prior predictive distribution inferred from `params`. The parameter `n` is the number of observations in the model.
