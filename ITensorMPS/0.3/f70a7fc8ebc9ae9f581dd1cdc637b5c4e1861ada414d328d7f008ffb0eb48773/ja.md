```
ortho_lims(::MPS/MPO)
```

MPS/MPOの直交中心のサイトの範囲を返します。

# 例

```julia
s = siteinds("S=½", 5)
ψ = random_mps(s)
ψ = orthogonalize(ψ, 3)

# ortho_lims(ψ) = 3:3
@show ortho_lims(ψ)

ψ[2] = random_itensor(inds(ψ[2]))

# ortho_lims(ψ) = 2:3
@show ortho_lims(ψ)
```
