```
BlockArray{T, N, R<:AbstractArray{<:AbstractArray{T,N},N}, BS<:Tuple{Vararg{AbstractUnitRange{<:Integer},N}}} <: AbstractBlockArray{T, N}
```

A `BlockArray` is an array where each block is stored contiguously. This means that insertions and retrieval of blocks can be very fast and non allocating since no copying of data is needed.

In the type definition, `R` defines the array type that holds the blocks, for example `Matrix{Matrix{Float64}}`.
