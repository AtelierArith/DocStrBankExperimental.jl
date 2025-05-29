```
HedgeG(xs, ys[, bootstrap]; [quantile=0.95])
```

2つのベクトル `xs` と `ys` の間のHedgeの $g$ 効果量指標を計算します。

効果量の信頼区間は `quantile` 分位点で計算されます。`bootstrap` が提供されている場合、信頼区間は `xs` と `ys` から `bootstrap` 回の再サンプリングによって計算されます。

$$
    g = \frac{m_A - m_B}{s}
$$

ここで、$m$ は平均、$s$ はプールされた標準偏差です：

$$
    s = \sqrt{\frac{(n_A - 1) s_A^2 + (n_B - 1) s_B^2}{n_A + n_B}}
$$

もし $m_A$ > $m_B$ であれば、$g$ は正の値になり、$m_A$ < $m_B$ であれば、$g$ は負の値になります。

!!! note
    `HedgeG` はサンプルサイズが < 20 の場合に `CohenD` よりも優れています。

