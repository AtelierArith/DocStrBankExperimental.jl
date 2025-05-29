```
index = ParetoSet(X[, sense])
```

Get the Pareto set from a given set of oberservations `X`. 

# Argument

  * `X::AbstractMatrix{Real}` size(X)=(n*objectives, n*samples)
  * `sense::AbstractVector{Union{Symbol, EGOSense}}=repeat(:Min, n_objectives)` sense of each objective, size(S)=(n_objectives,)
