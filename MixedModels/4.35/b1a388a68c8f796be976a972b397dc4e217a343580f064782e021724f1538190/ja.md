```
std(m::MixedModel)
```

ランダム効果の推定標準偏差を `Vector{Vector{T}}` として返します。

FIXME: これは古い慣習である isfinite(sdest(m)) を使用しています。おそらく m.σs に置き換えるべきです。
