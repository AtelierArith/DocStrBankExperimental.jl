```
Patience(; n=5)
```

損失報告反復アルゴリズムのための早期停止基準。

損失の連続した `n` 回の増加によって停止がトリガーされます。

[Prechelt, Lutz (1998): "Early Stopping- But When?", in *Neural Networks: Tricks of the Trade*, ed. G. Orr, Springer.](https://link.springer.com/chapter/10.1007%2F3-540-49430-8_3) において "*UP*s" として示されています。

カスタマイズ可能な損失ベースの停止基準を使用するには、`stop_if_true=true` オプションを持つ [`WithLossDo`](@ref) または [`WithTrainingLossesDo`](@ref) を使用してください。
