```
AntiDiagonalOperator{N,T<:Complex}<:AbstractOperator
```

A structure representing an anti-diagonal quantum `Operator` (i.e., a complex matrix of element type T, with non-zero elements all lying on the cross-diagonal). The equivalent dense matrix would have size NxN.

# Examples

```jldoctest
julia> AntiDiagonalOperator([1, 2])
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    2.0 + 0.0im    .

```
