```julia
struct SemiMarkov{A<:BaytesFilters.SemiMarkovInitiation, B<:BaytesFilters.SemiMarkovTransition, C} <: BaytesFilters.ParticleKernel
```

セミマルコフカーネルによる粒子の伝播。

# フィールド

  * `initial::BaytesFilters.SemiMarkovInitiation`: 初期分布、iterの関数。
  * `transition::BaytesFilters.SemiMarkovTransition`: 遷移分布、全粒子軌道と現在の反復カウントの関数。
  * `evidence::Any`: 粒子に重みを付けるデータ分布。全データ、粒子軌道、現在の反復カウントの関数。
