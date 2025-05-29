```
SwapLikeOperator{N,T<:Complex}<:AbstractOperator
```

A structure representing a quantum operator performing a "swap" operation, with element type T. A `phase` value is applied to the swapped qubit coefficients. This operator is always of size 4x4.

For example, the iswap `Operator` can be built using a `phase=0.0 + 1.0im` by calling:

```jldoctest
julia> SwapLikeOperator(0.0 + 1.0im)
(4, 4)-element Snowflurry.SwapLikeOperator:
Underlying data ComplexF64:
Equivalent DenseOperator:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 1.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 1.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im

```
