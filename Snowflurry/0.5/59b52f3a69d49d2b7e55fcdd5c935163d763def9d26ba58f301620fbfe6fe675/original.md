```
IdentityOperator{N,T<:Complex}<:AbstractOperator
```

A structure representing the identity quantum operator, with element type T. This operator is always of size 2x2.

# Example

```jldoctest
julia> IdentityOperator()
(2, 2)-element Snowflurry.IdentityOperator:
Underlying data ComplexF64:
Equivalent DenseOperator:
1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im

```
