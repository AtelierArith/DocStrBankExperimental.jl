```
sim_cfbd(t  ::Float64,
         λ  ::Float64,
         μ  ::Float64,
         ψ  ::Vector{Float64},
         ψts::Vector{Float64})
```

高さ `t` の定常化石出生-死亡 `iTree` を、種分化率 `λ`、絶滅率 `μ`、および化石化率のベクトル `ψ` を用いてシミュレートします。
