```
entropy_distribution(x; τ = 1, m = 3, n = 3, base = 2)
```

Compute the distribution entropy [Li2015](@cite) of `x` using embedding dimension `m` with delay/lag `τ`, using the Chebyshev distance metric, and using an `n`-element equally-spaced binning over the distribution of distances to estimate probabilities.

This function is just a convenience call to:

```julia
x = rand(1000000)
o = SequentialPairDistances(x, n, m, τ, metric = Chebyshev())
h = information(Shannon(base = 2), o, x)
```

See [`SequentialPairDistances`](@ref) for more info.
