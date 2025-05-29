```julia
struct ParameterWeights
```

現在の時間ステップ t における重みと正規化された粒子の重みのコンテナです。

# フィールド

  * `ℓweights::Vector{Float64}`: 対数尤度計算に使用されます。
  * `ℓweightsₙ::Vector{Float64}`: resampling 粒子とサンプリング軌道に使用される exp(ℓweightsₙ) ~ 数値的安定性のために対数空間に保持されます。
  * `buffer::Vector{Float64}`: ℓweights と ℓweightsₙ と同じサイズのバッファベクターです。
