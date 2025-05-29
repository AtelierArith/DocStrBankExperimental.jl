```
evaluate!(buffer::AbstractArray{T,N}, sampling, al; dim=1) where {T,N}
```

Like [`evaluate`](@ref), but write the result to `buffer`. Please use dim = 1 or N to avoid allocating large temporary arrays internally.
