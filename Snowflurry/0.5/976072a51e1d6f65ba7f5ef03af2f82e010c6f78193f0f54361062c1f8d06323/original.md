```
get_num_bodies(x::Union{Ket, Bra}, hilbert_space_size_per_body=2)
```

Returns the number of bodies associated with a `Ket` or a `Bra` given the `hilbert_space_size_per_body`.

# Examples

```jldoctest
julia> ψ = Ket([1., 0., 0., 0., 0., 0., 0., 0., 0.])
9-element Ket{ComplexF64}:
1.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im


julia> get_num_bodies(ψ, 3)
2

```
