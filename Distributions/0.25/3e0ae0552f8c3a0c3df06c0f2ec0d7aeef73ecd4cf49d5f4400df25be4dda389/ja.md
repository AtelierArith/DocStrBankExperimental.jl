```
Laplace(μ,θ)
```

*ラプラス分布*は、位置 `μ` とスケール `θ` を持ち、確率密度関数は次のようになります。

$$
f(x; \mu, \theta) = \frac{1}{2 \theta} \exp \left(- \frac{|x - \mu|}{\theta} \right)
$$

```julia
Laplace()       # 位置がゼロでスケールが単位のラプラス分布、すなわち Laplace(0, 1)
Laplace(μ)      # 位置が μ でスケールが単位のラプラス分布、すなわち Laplace(μ, 1)
Laplace(μ, θ)   # 位置が μ でスケールが θ のラプラス分布

params(d)       # パラメータを取得、すなわち (μ, θ)
location(d)     # 位置パラメータを取得、すなわち μ
scale(d)        # スケールパラメータを取得、すなわち θ
```

外部リンク

  * [ラプラス分布 - Wikipedia](http://en.wikipedia.org/wiki/Laplace_distribution)
