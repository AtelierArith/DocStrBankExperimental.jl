```
get_num_qubits(x::Union{Ket, Bra})
```

Returns the number of qubits associated with a `Ket` or a `Bra`.

# Examples

```jldoctest
julia> ψ = Ket([1., 0., 0., 0.])
4-element Ket{ComplexF64}:
1.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im


julia> get_num_qubits(ψ)
2

```
