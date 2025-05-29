```
TwoParticleExcitation(i, j, k, l) <: AbstractOperator
```

二粒子縮小密度行列の ${ij, kl}$ 要素を表します：

$$
ρ̂^{(2)}_{ij, kl} =  â^†_{i} â^†_{j} â_{l} â_{k}
$$

ここで `i`、`j`、`k`、および `l`（すべて `<: Int`）はモード番号を指定します。

# 参照

  * [`single_particle_density`](@ref)
  * [`SingleParticleDensity`](@ref)
  * [`SingleParticleExcitation`](@ref)
