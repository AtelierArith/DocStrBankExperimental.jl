```
train_flow([rng::AbstractRNG, ]vo, flow, args...; kwargs...)
```

与えられた正規化フロー `flow` を `optimize` を呼び出すことで訓練します。

# 引数

  * `rng::AbstractRNG`: 擬似乱数生成器
  * `vo`: 変分目的
  * `flow`: 訓練される正規化フロー、`<:Bijectors.TransformedDistribution` として定義することを推奨します
  * `args...`: `vo` の追加引数

# キーワード引数

  * `max_iters::Int=1000`: 最大反復回数
  * `optimiser::Optimisers.AbstractRule=Optimisers.ADAM()`: ステップを計算するための最適化手法
  * `ADbackend::ADTypes.AbstractADType=ADTypes.AutoZygote()`: 自動微分バックエンド、現在は `ADTypes.AutoZygote()`, `ADTypes.ForwardDiff()`, `ADTypes.ReverseDiff()`, `ADTypes.AutoMooncake()` および `ADTypes.AutoEnzyme(;       mode=Enzyme.set_runtime_activity(Enzyme.Reverse),       function_annotation=Enzyme.Const,   )` をサポートしています。ユーザーが `AutoEnzyme` を使用したい場合は、上記のように `set_runtime_activity` と `function_annotation` を含めることを確認してください。
  * `kwargs...`: `optimize` のための追加キーワード引数（詳細は [`optimize`](@ref) を参照）

# 戻り値

  * `flow_trained`: 訓練された正規化フロー
  * `opt_stats`: 訓練プロセス中の最適化手法の統計（詳細は [`optimize`](@ref) を参照）
  * `st`: 訓練の継続の可能性のための最適化手法の状態
