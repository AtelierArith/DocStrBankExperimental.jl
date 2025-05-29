```
normalize!(h::Histogram{T,N}, aux_weights::Array{T,N}...; mode::Symbol=:pdf) where {T<:AbstractFloat,N}
```

Normalize the histogram `h` and optionally scale one or more auxiliary weight arrays appropriately. See description of `normalize` for details. Returns `h`.
