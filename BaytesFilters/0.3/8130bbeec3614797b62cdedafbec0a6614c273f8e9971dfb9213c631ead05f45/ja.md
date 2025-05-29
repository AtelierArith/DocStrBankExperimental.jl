```julia
struct ParticleBuffer{A, I, P}
```

粒子伝播中のアロケーションを避けるための一時的なバッファ値を含みます。

# フィールド

  * `parameter::BaytesCore.ParameterBuffer{A, I} where {A, I}`: 一回のイテレーションのための粒子と祖先のバッファ値を含みます。
  * `proposal::Vector`: 提案された軌道と予測された潜在変数。
  * `prediction::Vector`: 予測された潜在データと観測データ。
  * `resampled::Vector{Bool}`: 各イテレーションで再サンプリングされたかどうかのブール値を格納します。
  * `ℓobjectiveᵥ::Vector{Float64}`: 各イテレーションのための増分対数ターゲット推定値を格納します。
