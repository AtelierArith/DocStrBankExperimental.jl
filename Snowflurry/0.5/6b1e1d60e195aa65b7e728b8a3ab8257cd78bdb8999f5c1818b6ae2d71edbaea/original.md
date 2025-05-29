```
get_embed_operator(op::DenseOperator, target_body_index::Int, system::MultiBodySystem)
```

Uses a local operator (`op`), which is defined for a particular body (e.g. qubit) with index `target_body_index`, to build the corresponding operator for the Hilbert space of the multi-body system given by `system`. 

# Examples

```jldoctest
julia> system = MultiBodySystem(3, 2)
Snowflurry.Multibody system with 3 bodies
   Hilbert space structure:
   [2, 2, 2]

julia> x = sigma_x()
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .

julia> X_1 = get_embed_operator(x, 1, system)
(8, 8)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im


```
