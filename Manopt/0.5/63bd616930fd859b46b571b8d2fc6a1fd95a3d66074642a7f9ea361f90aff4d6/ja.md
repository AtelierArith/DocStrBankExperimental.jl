```
AbstractManoptSolverState
```

すべてのソルバーステートの一般的なスーパタイプです。

# フィールド

以下のフィールドはデフォルトであると想定されています。異なるフィールドを使用する場合は、アクセス関数 [`get_iterate`](@ref) と [`get_stopping_criterion`](@ref) をそれに応じて調整してください。

  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
