```
DensityMatrixDiagonal(mode; component=0) <: AbstractHamiltonian
```

単一粒子密度の対角要素を表します：

$$
\hat{n}_{i,σ} = \hat a^†_{i,σ} \hat a_{i,σ}
$$

ここで、$i$ は `mode` で、$σ$ は `component` です。`component` がゼロの場合、すべてのコンポーネントの合計が計算されます。

# 参照

  * [`single_particle_density`](@ref)
  * [`SingleParticleDensity`](@ref)
  * [`SingleParticleExcitation`](@ref)
