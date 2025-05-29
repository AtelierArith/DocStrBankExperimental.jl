```
rand(alg, dims::Tuple{Vararg{Int64,2}}; mask=nothing) where {T <: Integer}
```

Creates a landscape of size `dims` (a tuple of two integers) following the model defined by `alg`. The `mask` argument accepts a matrix of boolean values, and is passed to `mask!` if it is not `nothing`. 
