# hpdi

高密度領域を計算します。

```julia
hpdi(x; alpha)

```

MCMCChains.jlの`hpd`から派生しています。

デフォルトでは、α=0.11で、両側の尾の面積がp < 0.055%およびp > 0.945%です。
