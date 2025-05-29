# 拡張ヘルプ

```
ρ(d::AbstractVector, B::AbstractBallp)
```

### アルゴリズム

ボール $B$ の中心を $c$、半径を $r$ とし、p-ノルムにおいて、$q = \frac{p}{p-1}$ とします。すると：

$$
ρ(d, B) = ⟨d, c⟩ + r ‖d‖_q.
$$
