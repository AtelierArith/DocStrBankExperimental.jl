```
InvalidValue()
```

損失報告反復アルゴリズムのための早期停止基準。

損失（またはトレーニング損失）が `NaN`、`Inf`、または `-Inf` の場合（または、より正確には、`isnan(loss)` または `isinf(loss)` が `true` の場合）に停止します。

カスタマイズ可能な損失ベースの停止基準を使用するには、`stop_if_true=true` オプションを使用して [`WithLossDo`](@ref) または [`WithTrainingLossesDo`](@ref) を使用してください。
