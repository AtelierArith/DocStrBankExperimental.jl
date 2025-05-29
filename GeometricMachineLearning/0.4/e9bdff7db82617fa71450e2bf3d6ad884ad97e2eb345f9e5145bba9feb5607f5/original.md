```
DataLoader(data::AbstractMatrix)
```

Make an instance of [`DataLoader`](@ref) based on a matrix.

# Arguments

See [`DataLoader(::AbstractArray{<:Number, 3})`](@ref) for details.

# Implementation

Internally the data are reshaped to a tensor of shape `(size(data)..., 1)` to make for a consistent representation.
