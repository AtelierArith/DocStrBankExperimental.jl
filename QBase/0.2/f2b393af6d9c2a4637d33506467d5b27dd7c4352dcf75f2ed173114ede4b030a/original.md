```
Ket(ψ :: Vector{T}; atol=ATOL :: Float64) where T <: Number
```

A normalized column vector on a complex-valued Hilbert space. If called with an adjoint vector `ψ'`, the adjoint will be taken on construction.

```julia
Ket(ψ :: Adjoint{Vector{T}}; atol=ATOL :: Float64) where T <: Number
```

Similarly a `Bra` can be converted into a `Ket` via the adjoint.

```julia
Ket(ψ :: Bra{T}; atol=ATOL :: Float64) where T <: Number
```

`Ket(ψ)`, throws a `DomainError` if `ψ` is not normalized.
