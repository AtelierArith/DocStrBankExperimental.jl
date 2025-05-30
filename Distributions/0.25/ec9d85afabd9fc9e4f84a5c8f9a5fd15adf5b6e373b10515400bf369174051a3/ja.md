```
Rayleigh(σ)
```

*レイリー分布*はスケール`σ`を持ち、確率密度関数は次のようになります。

$$
f(x; \sigma) = \frac{x}{\sigma^2} e^{-\frac{x^2}{2 \sigma^2}}, \quad x > 0
$$

これは、$X, Y \sim \operatorname{Normal}(0,\sigma)$が独立であるとき、$\sqrt{X^2 + Y^2} \sim \operatorname{Rayleigh}(\sigma)$という性質を通じて[`Normal`](@ref)分布に関連しています。

```julia
Rayleigh()       # 単位スケールのレイリー分布、すなわち Rayleigh(1)
Rayleigh(σ)      # スケール σ のレイリー分布

params(d)        # パラメータを取得、すなわち (σ,)
scale(d)         # スケールパラメータを取得、すなわち σ
```

外部リンク

  * [レイリー分布 - Wikipedia](http://en.wikipedia.org/wiki/Rayleigh_distribution)
