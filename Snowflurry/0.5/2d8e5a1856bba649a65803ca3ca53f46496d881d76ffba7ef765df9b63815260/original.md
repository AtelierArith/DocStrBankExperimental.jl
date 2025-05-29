```
SparseOperator{N,T<:Complex}<:AbstractOperator
```

A structure representing a quantum operator with a sparse (CSR) matrix representation, with element type T. The equivalent dense matrix would have size NxN.

!!! warning
    The `apply_operator()` method is not implemented for this operator type. Try using `DenseOperator` instead.


# Examples

```jldoctest
julia> z = SparseOperator([-1.0 1.0;0.0 -1.0])
(2, 2)-element Snowflurry.SparseOperator:
Underlying data ComplexF64:
 -1.0 + 0.0im   1.0 + 0.0im
       ⋅       -1.0 + 0.0im

```
