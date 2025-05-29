```
log(M::AbstractManifold, p, q)
```

Compute the logarithmic map of point `q` at base point `p` on the [`AbstractManifold`](@ref) `M`. The logarithmic map is the inverse of the [`exp`](@ref)onential map. Note that the logarithmic map might not be globally defined.

See also [`inverse_retract`](@ref).
