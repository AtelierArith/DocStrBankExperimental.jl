```
Normal(μ,σ)
```

*正規分布*は、平均`μ`および標準偏差`σ≥0`を持ち、確率密度関数は次のようになります。

$$
f(x; \mu, \sigma) = \frac{1}{\sqrt{2 \pi \sigma^2}}
\exp \left( - \frac{(x - \mu)^2}{2 \sigma^2} \right)
$$

`σ == 0`の場合、分布は`μ`に集中した点質量になります。技術的には連続分布ではありませんが、`σ`がアンダーフローした場合を考慮するために許可されており、関数は$σ → 0$の点wise limitを取ることによって定義されます。

```julia
Normal()          # 平均0、分散1の標準正規分布
Normal(μ)         # 平均μ、分散1の正規分布
Normal(μ, σ)      # 平均μ、分散σ^2の正規分布

params(d)         # パラメータを取得、すなわち(μ, σ)
mean(d)           # 平均を取得、すなわちμ
std(d)            # 標準偏差を取得、すなわちσ
```

外部リンク

  * [正規分布 - Wikipedia](http://en.wikipedia.org/wiki/Normal_distribution)
