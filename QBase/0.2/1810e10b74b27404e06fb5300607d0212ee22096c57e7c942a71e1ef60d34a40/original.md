```
Bra(ψ :: Adjoint{T,Vector{T}}; atol=ATOL :: Float64) where T <: Number
```

A row vector on a complex valued HIlbet space. Bras are dual to Kets via the adjoint If called with an `Vector{<:Number}` type, the adjoint will automatically be taken `ψ'`.

```julia
Bra(ψ :: Vector{<:Number}; atol=ATOL :: Float64)
```

Similarly a `Ket` can be converted into a `Bra` via the adjoint.

```julia
Bra(ψ :: Ket; atol=ATOL :: Float64)
```

`Bra(ψ')`, throws a `DomainError` if `ψ'` is not normalized.
