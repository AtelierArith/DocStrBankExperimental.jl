```
Levy(μ, σ)
```

*レヴィ分布*は、位置 `μ` とスケール `σ` を持ち、確率密度関数は次のようになります。

$$
f(x; \mu, \sigma) = \sqrt{\frac{\sigma}{2 \pi (x - \mu)^3}}
\exp \left( - \frac{\sigma}{2 (x - \mu)} \right), \quad x > \mu
$$

```julia
Levy()         # 位置がゼロでスケールが単位のレヴィ分布、すなわち Levy(0, 1)
Levy(μ)        # 位置 μ でスケールが単位のレヴィ分布、すなわち Levy(μ, 1)
Levy(μ, σ)     # 位置 μ とスケール σ のレヴィ分布

params(d)      # パラメータを取得、すなわち (μ, σ)
location(d)    # 位置パラメータを取得、すなわち μ
```

外部リンク

  * [Lévy distribution on Wikipedia](http://en.wikipedia.org/wiki/Lévy_distribution)
