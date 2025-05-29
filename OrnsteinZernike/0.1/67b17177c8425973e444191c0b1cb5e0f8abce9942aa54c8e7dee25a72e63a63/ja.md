```
LennardJones
```

レナード・ジョーンズペア相互作用を実装します $u(r) = 4\epsilon [(\sigma/r)^{12} - (\sigma/r)^6]$。

それぞれポテンシャルの強さと粒子サイズである値 `ϵ` と `σ` を期待します。

例：

```julia
potential = LennardJones(1.0, 2.0)
```
