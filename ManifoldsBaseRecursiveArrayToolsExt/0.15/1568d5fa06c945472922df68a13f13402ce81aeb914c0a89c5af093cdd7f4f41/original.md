```
getindex(p, M::ProductManifold, i::Union{Integer,Colon,AbstractVector})
p[M::ProductManifold, i]
```

Access the element(s) at index `i` of a point `p` on a [`ProductManifold`](@ref) `M` by linear indexing. See also [Array Indexing](https://docs.julialang.org/en/v1/manual/arrays/#man-array-indexing-1) in Julia.
