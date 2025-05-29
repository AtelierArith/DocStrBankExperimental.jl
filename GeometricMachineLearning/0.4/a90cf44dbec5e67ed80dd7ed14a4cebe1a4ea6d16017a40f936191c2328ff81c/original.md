```
MomentumCache(Y)
```

Store the moment for `Y` (initialized as zeros).

The moment is called `B`.

If the cache is called with an instance of a [`Manifold`](@ref) it initializes the moments as elements of $\mathfrak{g}^\mathrm{hor}$ ([`AbstractLieAlgHorMatrix`](@ref)).

See [`AdamCache`](@ref).
