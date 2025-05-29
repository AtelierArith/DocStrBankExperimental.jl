```
get_num_bodies(x::AbstractOperator, hilbert_space_size_per_body=2)
```

Returns the number of bodies associated with an `Operator` given the `hilbert_space_size_per_body`.

# Examples

```jldoctest
julia> ρ = DenseOperator([1. 0. 0.
                          0. 0. 0.
                          0. 0. 0.])
(3, 3)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im

julia> get_num_bodies(ρ, 3)
1

```
