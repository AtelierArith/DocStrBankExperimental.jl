```
deepview(A::AbstractArray, idxs...)
deepview(A::AbstractArray{<:AbstractArray, N}, idxs...) where {N}
```

Recursive `view` on flat or nested arrays. If A is an array of arrays, uses the first `N` entries in `idxs` on `A`, then the rest on the inner array(s). If A is not a nested array, `deepview` is equivalent to `view`.

See also [`deepgetindex`](@ref) and [`deepsetindex!`](@ref).
