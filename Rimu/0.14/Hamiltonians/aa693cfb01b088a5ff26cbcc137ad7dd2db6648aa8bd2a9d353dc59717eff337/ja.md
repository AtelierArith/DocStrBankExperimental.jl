```
SingleParticleExcitation(i, j) <: AbstractOperator
```

単一粒子縮小密度行列の ${i,j}$ 要素を表します：

$$
ρ̂^{(1)}_{i,j} = â^†_{i} â_{j}
$$

ここで `i <: Int` と `j <: Int` はモード番号を指定します。

# 参照

  * [`single_particle_density`](@ref)
  * [`SingleParticleDensity`](@ref)
  * [`TwoParticleExcitation`](@ref)
