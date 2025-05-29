```
inner(M::AbstractPowerManifold, p, X, Y)
```

Compute the inner product of `X` and `Y` from the tangent space at `p` on an [`AbstractPowerManifold`](@ref) `M`, i.e. for each arrays entry the tangent vector entries from `X` and `Y` are in the tangent space of the corresponding element from `p`. The inner product is then the sum of the elementwise inner products.
