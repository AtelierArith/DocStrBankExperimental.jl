```
PVM( Π :: Vector{Vector{T}}; atol=ATOL :: Float64 ) <: Measurement{T}
```

The concret type for a projector-valued measure. The projectors are represented as a set of orthonormal basis vectors

A `DomainError` is thrown if `Π` does not contain an orthonormal basis.
