```
Landau(μ,θ)
```

*ランドー分布*は、位置 `μ` とスケール `θ` を持ち、確率密度関数は次のようになります。

$$
p(x) = \frac{1}{2 \pi i} \int_{\mu-i\infty}^{\mu+i\infty} e^{s \log(s) + x s}\, ds
$$

```julia
Landau()       # 位置がゼロでスケールが単位のランドー分布、すなわち Landau(0, 1)
Landau(u)      # 位置が u でスケールが単位のランドー分布、すなわち Landau(u, 1)
Landau(u, b)   # 位置が u でスケールが b のランドー分布

params(d)       # パラメータを取得、すなわち (u, b)
location(d)     # 位置パラメータを取得、すなわち u
scale(d)        # スケールパラメータを取得、すなわち b
```

外部リンク

  * [ランドー分布のウィキペディア](http://en.wikipedia.org/wiki/Landau_distribution)
