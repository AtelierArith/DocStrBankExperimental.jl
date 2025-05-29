```julia
struct ParticleFilterTune{T<:ModelWrappers.Tagged, A<:BaytesCore.ParameterWeighting, B<:BaytesCore.ResamplingMethod, C<:BaytesFilters.ParticleReferencing, D, E, F, G, U<:BaytesCore.UpdateBool} <: BaytesCore.AbstractTune
```

パーティクルフィルタのチューニング情報を保持します。

# フィールド

  * `tagged::ModelWrappers.Tagged`: タグ付きモデルパラメータ。
  * `weighting::BaytesCore.ParameterWeighting`: パーティクルの重み付け方法。
  * `resampling::BaytesCore.ResamplingMethod`: パーティクルの軌跡の再サンプリング方法。
  * `referencing::BaytesFilters.ParticleReferencing`: 各イテレーションの最後のパーティクルの参照タイプ - 条件付き、系譜的、または周辺実装のいずれか。
  * `config::BaytesFilters.ParticleFilterConfig`: データと参照サイズおよびソートを含みます。
  * `chains::BaytesCore.ChainsTune`: パーティクルチェーンの数とチューニング情報。
  * `memory::BaytesFilters.ParticleFilterMemory`: 潜在データと観測データのためのメモリ。
  * `generated::BaytesCore.UpdateBool`: サンプリング中に生成された量を生成するかどうかのブール値。
  * `iter::BaytesCore.Iterator`: 現在のイテレーション。
