```
CohenD(xs, ys[, bootstrap]; [quantile=0.95])
```

2つのベクトル `xs` と `ys` の間のCohenの $d$ 効果量指数を計算します。

効果量の信頼区間は `quantile` 分位点で計算されます。`bootstrap` が提供されると、信頼区間は `xs` と `ys` から `bootstrap` 回の再サンプリングによって計算されます。

$$
    d = \frac{m_A - m_B}{s}
$$

ここで、$m$ は平均、$s$ はプールされた標準偏差です：

$$
    s = \sqrt{\frac{(n_A - 1) s_A^2 + (n_B - 1) s_B^2}{n_A + n_B - 2}}
$$

もし $m_A$ > $m_B$ であれば、$d$ は正の値になり、$m_A$ < $m_B$ であれば、$d$ は負の値になります。

!!! note
    サンプルサイズが < 20 の場合、`HedgeG` は `CohenD` よりも優れています。


# 例

```julia
xs = randn(100000)
ys = randn(100000) .+ 0.01

using EffectSizes
CohenD(xs, ys)

using HypothesisTests
EqualVarianceTTest(xs, ys)
```
