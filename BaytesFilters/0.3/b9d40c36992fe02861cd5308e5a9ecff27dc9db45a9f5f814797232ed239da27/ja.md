```julia
struct ParticleFilterDefault{M<:Union{Nothing, BaytesFilters.ParticleFilterMemory}, A<:BaytesCore.ParameterWeighting, B<:BaytesCore.ResamplingMethod, C<:BaytesFilters.ParticleReferencing, T<:Integer, I<:ModelWrappers.AbstractInitialization, U<:BaytesCore.UpdateBool}
```

Particle Filter コンストラクタのデフォルト引数。

# フィールド

  * `memory::Union{Nothing, BaytesFilters.ParticleFilterMemory}`: 粒子とデータのためのメモリ。
  * `weighting::BaytesCore.ParameterWeighting`: 粒子のための重み付け方法。
  * `resampling::BaytesCore.ResamplingMethod`: 粒子の軌跡のための再サンプリング方法。
  * `referencing::BaytesFilters.ParticleReferencing`: 各イテレーションでの最後の粒子の参照タイプ - 条件付き、祖先、または周辺実装のいずれか。
  * `coverage::Float64`: 粒子/データポイントのカバレッジ。
  * `threshold::Float64`: 粒子の軌跡の再サンプリングのためのESS閾値。
  * `ancestortype::Type{T} where T<:Integer`: 祖先インデックスのための型。
  * `init::ModelWrappers.AbstractInitialization`: 初期モデルパラメータを取得するためのメソッド、'AbstractInitialization'を参照。
  * `generated::BaytesCore.UpdateBool`: 対応するモデルのためにgenerate(_rng, objective)がPF Diagnosticsに保存されているかどうかのブール値。
