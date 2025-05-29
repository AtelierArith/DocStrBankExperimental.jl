```
SymTriangularDist(μ, σ)
```

*対称三角分布*は、位置 `μ` とスケール `σ` を持ち、確率密度関数は次のようになります。

$$
f(x; \mu, \sigma) = \frac{1}{\sigma} \left( 1 - \left| \frac{x - \mu}{\sigma} \right| \right), \quad \mu - \sigma \le x \le \mu + \sigma
$$

```julia
SymTriangularDist()         # 位置がゼロでスケールが単位の対称三角分布
SymTriangularDist(μ)        # 位置 μ でスケールが単位の対称三角分布
SymTriangularDist(μ, s)     # 位置 μ でスケール σ の対称三角分布

params(d)       # パラメータを取得します。すなわち (μ, σ)
location(d)     # 位置パラメータを取得します。すなわち μ
scale(d)        # スケールパラメータを取得します。すなわち σ
```
