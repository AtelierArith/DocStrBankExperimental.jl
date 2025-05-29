```
shortest_geodesic!(M::AbstractManifold, p, q) -> Function
```

Get a [`geodesic`](@ref) $γ_{p,q}(t)$ whose length is the shortest path between the points `p`and `q`, where $γ_{p,q}(0)=p$ and $γ_{p,q}(1)=q$. When there are multiple shortest geodesics, a deterministic choice will be returned.

This function returns a function `(r,t) -> ...` of time `t` which works in place of `r`.

Further variants

```
shortest_geodesic!(M::AabstractManifold, r, p, q, t::Real)
shortest_geodesic!(M::AbstractManifold, R, p, q, T::AbstractVector) -> AbstractVector
```

mutate (and return) the point `r` and the vector of points `R`, respectively, returning the point at time `t` or points at times `t` in `T` along the shortest [`geodesic`](@ref).
