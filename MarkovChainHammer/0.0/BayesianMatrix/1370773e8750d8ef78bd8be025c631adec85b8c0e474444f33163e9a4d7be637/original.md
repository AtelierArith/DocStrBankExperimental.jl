```
unpack(Q::BayesianGenerator)
```

Unpack a BayesianGenerator object into its parameters.

# Arguments

  * `Q::BayesianGenerator`: The BayesianGenerator object to unpack.

# Returns

  * `Tuple{NamedTuple{(:prior, :posterior, :predictive),Tuple{NamedTuple{(:α, :β, :αs),Tuple{Vector{Float64},Vector{Float64},Vector{Float64}}},NamedTuple{(:α, :β, :αs),Tuple{Vector{Float64},Vector{Float64},Vector{Float64}}},NamedTuple{(:μ, :σ, :ξ, :n, :αs),Tuple{Vector{Float64},Vector{Float64},Vector{Float64},Vector{Int64},Vector{Vector{Float64}}}}}}}`: A tuple containing the parameters for the prior, posterior and predictive distributions.
