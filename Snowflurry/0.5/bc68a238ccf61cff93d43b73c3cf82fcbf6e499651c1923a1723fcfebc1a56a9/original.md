```
tr(A::AbstractOperator)
```

Compute the trace of Operator `A`.

# Examples

```jldoctest
julia> I = eye()
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im


julia> trace = tr(I)
2.0 + 0.0im

```
