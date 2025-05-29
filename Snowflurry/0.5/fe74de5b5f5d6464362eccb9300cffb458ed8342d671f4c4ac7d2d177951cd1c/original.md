```
is_hermitian(A::AbstractOperator)
```

Determine if Operator `A` is Hermitian (i.e., self-adjoint).

# Examples

```jldoctest
julia> Y = sigma_y()
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    0.0 - 1.0im
    0.0 + 1.0im    .


julia> is_hermitian(Y)
true

julia> P = sigma_p()
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    0.0 + 0.0im    .


julia> is_hermitian(P)
false

```
