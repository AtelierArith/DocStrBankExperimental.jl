```
Cauchy(μ, σ)
```

*コーシー分布*は、位置 `μ` とスケール `σ` を持ち、確率密度関数は次のようになります。

$$
f(x; \mu, \sigma) = \frac{1}{\pi \sigma \left(1 + \left(\frac{x - \mu}{\sigma} \right)^2 \right)}
$$

```julia
Cauchy()         # 標準コーシー分布、すなわち Cauchy(0, 1)
Cauchy(μ)        # 位置 μ と単位スケールのコーシー分布、すなわち Cauchy(μ, 1)
Cauchy(μ, σ)     # 位置 μ とスケール σ のコーシー分布

params(d)        # パラメータを取得、すなわち (μ, σ)
location(d)      # 位置パラメータを取得、すなわち μ
scale(d)         # スケールパラメータを取得、すなわち σ
```

外部リンク

  * [コーシー分布 - Wikipedia](http://en.wikipedia.org/wiki/Cauchy_distribution)
