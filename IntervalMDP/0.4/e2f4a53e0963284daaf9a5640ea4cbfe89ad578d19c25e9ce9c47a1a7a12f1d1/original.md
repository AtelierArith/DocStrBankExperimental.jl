```
InfiniteTimeSafety{R <: Real, VT <: Vector{<:CartesianIndex}}
```

`InfiniteTimeSafety` is similar to [`FiniteTimeSafety`](@ref) except that the time horizon is infinite, i.e., $H = \infty$. In practice it means, performing the value iteration until the value function has converged, defined by some threshold `convergence_eps`. The convergence threshold is that the largest value of the most recent Bellman residual is less than `convergence_eps`.
