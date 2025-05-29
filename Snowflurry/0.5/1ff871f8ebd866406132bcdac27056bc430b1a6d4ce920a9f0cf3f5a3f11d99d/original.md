```
commute(A::AbstractOperator, B::AbstractOperator)
```

Returns the commutation of `A` and `B`.

```jldoctest
julia> σ_x = sigma_x()
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .


julia> σ_y = sigma_y()
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    0.0 - 1.0im
    0.0 + 1.0im    .


julia> commute(σ_x, σ_y)
(2,2)-element Snowflurry.DiagonalOperator:
Underlying data type: ComplexF64:
0.0 + 2.0im    .
.    0.0 - 2.0im

```
