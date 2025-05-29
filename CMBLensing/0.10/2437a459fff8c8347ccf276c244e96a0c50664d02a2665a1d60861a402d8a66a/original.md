```
batch(fs::LambertField...)
batch(fs::Vector{<:LambertField})
```

Concatenate one of more LambertFields along the "batch" dimension (dimension 4 of the underlying array). For the inverse operation, see [`unbatch`](@ref). 
