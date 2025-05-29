```
exp!(M::AbstractManifold, q, p, X)
```

Compute the exponential map of tangent vector `X`, optionally scaled by `t`,  at point `p` from the manifold [`AbstractManifold`](@ref) `M`. The result is saved to `q`.

If you want to implement exponential map for your manifold, you should implement the in-place method with, that is `exp_fused!(M::MyManifold, q, p, X)`.

See also [`exp`](@ref).
