```
apply_instruction!(state::Ket, gate::Gate)
```

`gate`を適用することで`state`を更新します。

# 例

```jldoctest
julia> ψ_0 = fock(0, 2)
2-element Ket{ComplexF64}:
1.0 + 0.0im
0.0 + 0.0im


julia> apply_instruction!(ψ_0, sigma_x(1))
2-element Ket{ComplexF64}:
0.0 + 0.0im
1.0 + 0.0im

```
