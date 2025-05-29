```
fock_dm(i::Int64, hspace_size::Int64)
```

Returns the density matrix corresponding to the Fock base `i` defined in a Hilbert space of size `hspace_size`.

```jldoctest
julia> dm = fock_dm(0, 2)
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im


```
