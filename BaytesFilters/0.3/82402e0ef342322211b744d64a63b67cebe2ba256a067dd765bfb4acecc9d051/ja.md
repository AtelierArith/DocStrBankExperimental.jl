```julia
struct ParticleFilter{A<:BaytesFilters.Particles, B<:BaytesFilters.ParticleFilterTune} <: BaytesCore.AbstractAlgorithm
```

粒子、遷移カーネル、および粒子伝播に関連するすべての調整情報を含みます。

# フィールド

  * `particles::BaytesFilters.Particles`: 粒子の値とカーネル。
  * `tune::BaytesFilters.ParticleFilterTune`: 粒子の調整設定。
