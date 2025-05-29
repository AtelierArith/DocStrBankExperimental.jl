```
Gumbel(μ, θ)
```

*Gumbel（最大値）分布* は、位置 `μ` とスケール `θ` を持ち、確率密度関数は次のようになります。

$$
f(x; \mu, \theta) = \frac{1}{\theta} e^{-(z + e^{-z})},
\quad \text{ with } z = \frac{x - \mu}{\theta}
$$

```julia
Gumbel()            # 位置がゼロでスケールが単位のGumbel分布、すなわちGumbel(0, 1)
Gumbel(μ)           # 位置がμでスケールが単位のGumbel分布、すなわちGumbel(μ, 1)
Gumbel(μ, θ)        # 位置がμでスケールがθのGumbel分布

params(d)        # パラメータを取得、すなわち(μ, θ)
location(d)      # 位置パラメータを取得、すなわちμ
scale(d)         # スケールパラメータを取得、すなわちθ
```

外部リンク

  * [Gumbel distribution on Wikipedia](http://en.wikipedia.org/wiki/Gumbel_distribution)
