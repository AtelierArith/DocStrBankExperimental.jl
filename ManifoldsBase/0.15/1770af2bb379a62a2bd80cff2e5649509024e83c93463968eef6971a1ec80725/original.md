```
exp!(M::AbstractManifold, q, p, X)
exp!(M::AbstractManifold, q, p, X, t::Number = 1)
```

Compute the exponential map of tangent vector `X`, optionally scaled by `t`,  at point `p` from the manifold [`AbstractManifold`](@ref) `M`. The result is saved to `q`.

If you want to implement exponential map for your manifold, you should implement the method with `t`, that is `exp!(M::MyManifold, q, p, X, t::Number)`.

See also [`exp`](@ref).
