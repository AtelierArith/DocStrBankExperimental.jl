```
DenseOperator{N,T<:Complex}<:AbstractOperator
```

A structure representing a quantum operator with a full (dense) matrix representation of size NxN and containing elements of type T.

# Examples

```jldoctest
julia> z = DenseOperator([1.0 0.0;0.0 -1.0])
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    -1.0 + 0.0im

```

Alternatively:

```jldoctest
julia> z = rotation(π/2, -π/4)  
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.7071067811865476 + 0.0im    0.4999999999999999 - 0.5im
-0.4999999999999999 - 0.5im    0.7071067811865476 + 0.0im


```
