```
is_braket( ψ :: Vector; atol=ATOL :: Float64) :: Bool

is_braket(
    ψ :: Adjoint{T, Vector{T}};
    atol=ATOL :: Float64
) where T <: Number :: Bool
```

Returns `true` if vector `ψ` is a valid bra (or ket):

  * `ψ` is a real or complex-valued vector.
  * `ψ` is normalized with respect to the bra-ket inner prodcut (`ψ' * ψ == 1`).
