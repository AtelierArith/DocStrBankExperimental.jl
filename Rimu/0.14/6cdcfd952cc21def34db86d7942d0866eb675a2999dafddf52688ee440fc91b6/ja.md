```
SingleParticleDensity(; save_every=1, component) <: PostStepStrategy
```

[`PostStepStrategy`](@ref) は対角 [`single_particle_density`](@ref) を計算するためのものです。これは、同じ `eltype` を持つ `Tuple` を記録します。

毎タイムステップで密度を計算することは高コストになる可能性があります。このコストは、`save_every` 引数をより高い値に設定することで削減できます。値が設定されている場合、保存がスキップされたときにゼロのベクトルが記録されます。

アドレス型に複数のコンポーネントがある場合、`component` 引数を使用してコンポーネントごとに密度を計算できます。

密度は正規化されておらず、ベクトル `norm(⋅,2)` の二乗で割る必要があります。

# 参照

  * [`single_particle_density`](@ref)
  * [`DensityMatrixDiagonal`](@ref)
