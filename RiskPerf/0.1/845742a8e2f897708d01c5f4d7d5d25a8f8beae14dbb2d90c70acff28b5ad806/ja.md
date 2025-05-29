```
omega_ratio(returns, target_return)
```

この関数はオメガ比を計算します。すべてのリターンがターゲットリターン以上である場合、比率は `Inf` を返すことに注意してください。

# 数式

$$
\Omega = -\dfrac{ \mathbb{E}\left[ \text{max}(\text{returns} - \text{target\_return}, 0) \right] }{ \mathbb{E}\left[ \text{min}(\text{target\_return} - \text{returns}, 0) \right] }
$$

# 引数

  * `returns`:        資産リターンのベクトル。
  * `target_return`:  提供されたリターンと同じ頻度（例：日次）を持つベンチマークリターンのベクトルまたはスカラー値。
