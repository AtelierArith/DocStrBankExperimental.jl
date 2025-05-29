```
getindex(p, M::AbstractPowerManifold, i::Union{Integer,Colon,AbstractVector}...)
p[M::AbstractPowerManifold, i...]
```

Access the element(s) at index `[i...]` of a point `p` on an [`AbstractPowerManifold`](@ref) `M` by linear or multidimensional indexing. See also [Array Indexing](https://docs.julialang.org/en/v1/manual/arrays/#man-array-indexing-1) in Julia.
