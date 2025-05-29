```
shortest_geodesic(M::AabstractManifold, p, q, t::Real)
```

Evaluate a [`geodesic`](@ref) $γ_{p,q}(t)$ whose length is the shortest path between the points `p`and `q`, where $γ_{p,q}(0)=p$ and $γ_{p,q}(1)=q$ at time `t`. When there are multiple shortest geodesics, a deterministic choice will be returned.
