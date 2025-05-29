```
MLJModelInterface.training_losses(model::M, report)
```

もし `M` がトレーニング損失を計算する反復モデルタイプである場合、このメソッドを実装して、歴史的順序での損失の `AbstractVector` を返します。モデルがスコアを計算する場合は、スコアの符号を反転させる必要があります。

次のトレイトオーバーロードも必要です: `MLJModelInterface.supports_training_losses(::Type{<:M}) = true`。
