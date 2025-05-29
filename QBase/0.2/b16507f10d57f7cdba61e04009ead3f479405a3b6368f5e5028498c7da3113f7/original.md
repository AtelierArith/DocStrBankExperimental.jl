```
ChoiOp( Λ :: AbstractMatrix, dims :: Vector{Int} ) :: ChoiOp{<:Number}
ChoiOp( 𝒩 :: Function, dims :: Vector{Int} ) :: ChoiOp{ComplexF64}
```

Constructs the Choi operator representation of a quantum channel. If either a function `𝒩` or set of kraus operators is provided as input, the Choi matrix is constructed with the [`choi_matrix`](@ref) method.

The `ChoiOp` type contains the fields:

  * `M :: Matrix{<:Number}` - The Choi matrix.
  * `dims :: Vector{Int}` - The channel's input/output dimension `[dim_in, dim_out]`.

A `DomainError` is thrown if [`is_choi_matrix`](@ref) returns `false`.
