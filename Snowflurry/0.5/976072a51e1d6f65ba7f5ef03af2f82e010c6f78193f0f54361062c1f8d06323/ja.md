```
get_num_bodies(x::Union{Ket, Bra}, hilbert_space_size_per_body=2)
```

`Ket` または `Bra` に関連付けられたボディの数を、`hilbert_space_size_per_body` を考慮して返します。

# 例

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
