```
deepgetindex(A::AbstractArray, idxs...)
deepgetindex(A::AbstractArray{<:AbstractArray, N}, idxs...) where {N}
```

Recursive `getindex` on flat or nested arrays. If A is an array of arrays, uses the first `N` entries in `idxs` on `A`, then the rest on the inner array(s). If A is not a nested array, `deepgetindex` is equivalent to `getindex`.

See also [`deepsetindex!`](@ref) and [`deepview`](@ref).
