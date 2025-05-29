`DiffCache(u::AbstractArray, N::Int = ForwardDiff.pickchunksize(length(u)); levels::Int = 1)` `DiffCache(u::AbstractArray; N::AbstractArray{<:Int})`

Builds a `DiffCache` object that stores both a version of the cache for `u` and for the `Dual` version of `u`, allowing use of pre-cached vectors with forward-mode automatic differentiation. Supports nested AD via keyword `levels` or specifying an array of chunk_sizes.
