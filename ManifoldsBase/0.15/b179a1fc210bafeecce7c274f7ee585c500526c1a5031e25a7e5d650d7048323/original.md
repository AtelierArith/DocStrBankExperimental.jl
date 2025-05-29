```
mid_point!(M::AbstractManifold, q, p1, p2)
```

Calculate the middle between the two point `p1` and `p2` from manifold `M`. By default uses [`log`](@ref), divides the vector by 2 and uses [`exp!`](@ref). Saves the result in `q`.
