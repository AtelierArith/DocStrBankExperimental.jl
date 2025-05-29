```
getpointestimate(samples::MCMCResult; method = "MAP", loss = "VI")
```

Computes a point estimate from a vector of samples of cluster allocations by searching for a minimiser of the posterior expectation of some loss function.

# Arguments

  * `method::String`: must be one of the following -

```
- `"MAP"`: maximum a posteriori.
- `"MLE"`: maximum likelihood estimation.
- `"MPEL"`: minimum posterior expected loss.
`"MAP"` and `"MLE"` search among the MCMC samples for the clustering with the maximum log posterior and log likelihood respectively. `"MPEL"` searches for a clustering that minimises the posterior expected loss of some loss function specified by the `loss` argument. The search space is the set of samples in `samples`.
```

  * `loss`: Determines the loss function used for the `"MPEL"` method. Must be either be a string or a function. If specified as a string, must be one of `"binder"` (Binder loss), `"omARI"` (one minus the Adjusted Rand Index), `"VI"` (Variation of Information distance), or `"ID"` (Information Distance). If specified as a function, must have a method defined for `(x::Vector{Int}, y::Vector{Int}) -> Real`.

# Returns

Returns a tuple `(clust, i)` where `clust` is a clustering allocation in `samples` and `i` is its sample index.
