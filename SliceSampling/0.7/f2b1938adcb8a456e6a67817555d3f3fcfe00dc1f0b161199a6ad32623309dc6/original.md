```
RandPermGibbs(unislice)
```

Random permutation coordinate-wise Gibbs sampling strategy. This applies `unislice` coordinate-wise in a random order.

# Arguments

  * `unislice::Union{<:AbstractUnivariateSliceSampling,<:AbstractVector{<:AbstractUnivariateSliceSampling}}`: a single or a vector of univariate slice sampling algorithms.

When `unislice` is a vector of samplers, each slice sampler is applied to the corresponding coordinate of the target posterior. In that case, the `length(unislice)` must match the dimensionality of the posterior.
