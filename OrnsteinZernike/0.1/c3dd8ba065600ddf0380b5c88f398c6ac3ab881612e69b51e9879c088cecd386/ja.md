```
PowerLaw
```

パワー法則ペア相互作用 $u(r) = \epsilon (\sigma/r)^{n}$ を実装します。

それぞれポテンシャルの強さと粒子サイズである値 `ϵ`、`σ`、および `n` を期待します。

例:

```julia
potential = PowerLaw(1.0, 2.0, 8)
```
