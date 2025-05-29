```
allocate(a)
allocate(a, dims::Integer...)
allocate(a, dims::Tuple)
allocate(a, T::Type)
allocate(a, T::Type, dims::Integer...)
allocate(a, T::Type, dims::Tuple)
allocate(M::AbstractManifold, a)
allocate(M::AbstractManifold, a, dims::Integer...)
allocate(M::AbstractManifold, a, dims::Tuple)
allocate(M::AbstractManifold, a, T::Type)
allocate(M::AbstractManifold, a, T::Type, dims::Integer...)
allocate(M::AbstractManifold, a, T::Type, dims::Tuple)
```

Allocate an object similar to `a`. It is similar to function `similar`, although instead of working only on the outermost layer of a nested structure, it maps recursively through outer layers and calls `similar` on the innermost array-like object only. Type `T` is the new number element type [`number_eltype`](@ref), if it is not given the element type of `a` is retained. The `dims` argument can be given for non-nested allocation and is forwarded to the function `similar`.

It's behavior can be overridden by a specific manifold, for example power manifold with nested replacing representation can decide that `allocate` for `Array{<:SArray}` returns another `Array{<:SArray}` instead of `Array{<:MArray}`, as would be done by default.
