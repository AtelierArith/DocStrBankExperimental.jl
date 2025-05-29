```
log!(M::AbstractManifold, X, p, q)
```

Compute the logarithmic map of point `q` at base point `p` on the [`AbstractManifold`](@ref) `M`. The result is saved to `X`. The logarithmic map is the inverse of the [`exp!`](@ref)onential map. Note that the logarithmic map might not be globally defined.

see also [`log`](@ref) and [`inverse_retract!`](@ref),
