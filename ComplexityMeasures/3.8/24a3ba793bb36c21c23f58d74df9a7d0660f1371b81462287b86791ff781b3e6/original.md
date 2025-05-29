```
entropy_permutation(x; τ = 1, m = 3, base = 2)
```

Compute the permutation entropy of `x` of order `m` with delay/lag `τ`. This function is just a convenience call to:

```julia
est = OrdinalPatterns(; m, τ)
information(Shannon(base), est, x)
```

See [`OrdinalPatterns`](@ref) for more info. Similarly, one can use [`WeightedOrdinalPatterns`](@ref) or [`AmplitudeAwareOrdinalPatterns`](@ref) for the weighted/amplitude-aware versions.
