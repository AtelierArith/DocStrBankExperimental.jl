```
parallel_transport_to(M::AbstractManifold, p, X, q)
```

Compute the parallel transport of $X$ along the curve $c(t) = γ_{p,q}(t)$, i.e. the (assumed to be unique) [`geodesic`](@ref) $γ_{p,q}$ connecting `p` and `q`.
