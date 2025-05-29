```
NumberSinceBest(; n=6)
```

損失報告を行う反復アルゴリズムのための早期停止基準です。

停止は、これまでの損失の最小値からの制御への呼び出し回数が `n` に達したときにトリガーされます。

カスタマイズ可能な損失ベースの停止基準を使用するには、`stop_if_true=true` オプションを使用して [`WithLossDo`](@ref) または [`WithTrainingLossesDo`](@ref) を使用してください。
