```julia
struct Markov{A, B, C} <: BaytesFilters.ParticleKernel
```

粒子伝播のためのマルコフカーネル。

# フィールド

  * `initial::Any`: 初期分布、iterの関数のみ。
  * `transition::Any`: 遷移分布、全粒子軌道と現在の反復カウントの関数。
  * `evidence::Any`: 粒子に重みを付けるデータ分布。全データ、粒子軌道、現在の反復カウントの関数。
