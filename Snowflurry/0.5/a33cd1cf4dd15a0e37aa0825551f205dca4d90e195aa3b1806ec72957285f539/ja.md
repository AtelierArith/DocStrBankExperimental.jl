```
get_num_qubits(x::Union{Ket, Bra})
```

`Ket`または`Bra`に関連付けられた量子ビットの数を返します。

# 例

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
