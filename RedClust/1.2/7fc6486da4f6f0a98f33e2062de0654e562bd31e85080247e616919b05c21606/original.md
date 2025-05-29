```
sampledist(params::PriorHyperparamsList, type::String, numsamples = 1)::Vector{Float64}
```

Generate a vector of samples of length `numsamples` from the prior predictive distribution on the distances, as encapsulated in `params`. `type` must be either `"intercluster"` or `"intracluster"`.
