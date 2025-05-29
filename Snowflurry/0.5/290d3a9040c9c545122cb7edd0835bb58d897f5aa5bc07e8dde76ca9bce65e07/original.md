```
DiagonalOperator{N,T<:Complex}<:AbstractOperator
```

A structure representing a diagonal quantum `Operator` (i.e., a complex matrix of element type T, with non-zero elements all lying on the diagonal). The equivalent dense matrix would have size NxN.

# Examples

```jldoctest
julia> z = DiagonalOperator([1.0,-1.0])
(2,2)-element Snowflurry.DiagonalOperator:
Underlying data type: ComplexF64:
1.0 + 0.0im    .
.    -1.0 + 0.0im

julia> z = DiagonalOperator([1.0+im,1.0,1.0,0.0-im])
(4,4)-element Snowflurry.DiagonalOperator:
Underlying data type: ComplexF64:
1.0 + 1.0im    .    .    .
.    1.0 + 0.0im    .    .
.    .    1.0 + 0.0im    .
.    .    .    0.0 - 1.0im

```
