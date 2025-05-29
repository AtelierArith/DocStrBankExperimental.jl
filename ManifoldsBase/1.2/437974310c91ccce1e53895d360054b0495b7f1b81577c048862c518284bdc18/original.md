```
shortest_geodesic(M::AbstractManifold, p, q, T::AbstractVector) -> AbstractVector
```

Evaluate a [`geodesic`](@ref) $γ_{p,q}(t)$ whose length is the shortest path between the points `p`and `q`, where $γ_{p,q}(0)=p$ and $γ_{p,q}(1)=q$ at time points `T`. When there are multiple shortest geodesics, a deterministic choice will be returned.
