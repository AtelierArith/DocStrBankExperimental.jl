```
deepsetindex!(A::AbstractArray, x, idxs...)
deepsetindex!(A::AbstractArray{<:AbstractArray,N}, x, idxs...) where {N}
```

Recursive `setindex!` on flat or nested arrays. If A is an array of arrays, uses the first `N` entries in `idxs` on `A`, then the rest on the inner array(s). If A is not a nested array, `deepsetindex!` is equivalent to `setindex!`.

See also [`deepgetindex`](@ref) and [`deepview`](@ref).
