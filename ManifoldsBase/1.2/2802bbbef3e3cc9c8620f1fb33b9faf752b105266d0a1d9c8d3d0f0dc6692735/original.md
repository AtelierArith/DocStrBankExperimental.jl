```
copy(M::AbstractManifold, p)
```

Copy the value(s) from the point `p` on the [`AbstractManifold`](@ref) `M` into a new point. See [`allocate_result`](@ref) for the allocation of new point memory and [`copyto!`](@ref) for the copying.
