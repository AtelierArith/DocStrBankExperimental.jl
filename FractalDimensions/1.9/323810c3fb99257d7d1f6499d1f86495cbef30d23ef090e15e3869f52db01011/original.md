```
molteno_dim(X::AbstractStateSpaceSet; k0::Int = 10, q = 1.0, base = 2)
```

Return an estimate of the [`generalized_dim`](@ref) of `X` using the algorithm by [Molteno1993](@cite). This function is a simple utilization of the probabilities estimated by [`molteno_boxing`](@ref) so see that function for more details. Here the entropy of the probabilities is computed at each size, and a line is fitted in the entropy vs log(size) graph, just like in [`generalized_dim`](@ref).
