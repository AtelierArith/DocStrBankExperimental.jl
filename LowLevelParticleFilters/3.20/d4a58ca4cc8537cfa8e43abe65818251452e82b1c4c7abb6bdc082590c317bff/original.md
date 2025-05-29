```
mean_trajectory(sol::ParticleFilteringSolution)
mean_trajectory(x::AbstractMatrix, we::AbstractMatrix)
```

Compute the weighted mean along the trajectory of a particle-filter solution. Returns a matrix of size `T × nx`. If `x` and `we` are supplied, the weights are expected to be in the original space (not log space).

See also [`mode_trajectory`](@ref)
