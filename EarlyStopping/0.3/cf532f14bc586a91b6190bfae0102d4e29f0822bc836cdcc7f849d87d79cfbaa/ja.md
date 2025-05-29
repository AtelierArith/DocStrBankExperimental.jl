```
Threshold(; value=0.0)
```

損失報告の反復アルゴリズムに対する早期停止基準です。

損失が `value` を下回るとすぐに停止がトリガーされます。

カスタマイズ可能な損失ベースの停止基準を使用するには、`stop_if_true=true` オプションを使用して [`WithLossDo`](@ref) または [`WithTrainingLossesDo`](@ref) を使用してください。
