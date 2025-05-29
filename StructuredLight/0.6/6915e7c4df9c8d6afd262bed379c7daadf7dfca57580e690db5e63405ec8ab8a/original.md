```
diagonal_hg(x, y, z=zero(eltype(x)); m=0, n=0, w=one(eltype(x)), k=one(eltype(x)))
```

Compute a diagonal Hermite-Gaussian mode. It is calculated by setting `θ=π/4` in [`hg`](@ref).

See also [`lg`](@ref).
