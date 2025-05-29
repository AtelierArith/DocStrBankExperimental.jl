```
GlassΔ(treatment, control[, bootstrap]; [quantile=0.95])
```

2つのベクトル`treatment`と`control`の間のGlassの$Δ$効果量指数を計算します。

効果量の信頼区間は`quantile`分位点で計算されます。`bootstrap`が提供されている場合、信頼区間は`xs`と`ys`から`bootstrap`回の再サンプリングによって計算されます。

$$
    Δ = \frac{m_T - m_C}{s_C}
$$

ここで、$m$は平均、$s$は標準偏差、$T$は治療群、$C$は対照群です。

もし$m_T$ > $m_C$であれば、$Δ$は正となり、$m_T$ < $m_C$であれば、$Δ$は負となります。

!!! note
    標準偏差が2つのグループ間で非常に異なる場合は`GlassΔ`を使用するべきです。

