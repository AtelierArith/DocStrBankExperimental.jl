```
Logistic(μ,θ)
```

*ロジスティック分布*は、位置`μ`とスケール`θ`を持ち、確率密度関数は次のようになります。

$$
f(x; \mu, \theta) = \frac{1}{4 \theta} \mathrm{sech}^2
\left( \frac{x - \mu}{2 \theta} \right)
$$

```julia
Logistic()       # 位置がゼロでスケールが単位のロジスティック分布、すなわちLogistic(0, 1)
Logistic(μ)      # 位置がμでスケールが単位のロジスティック分布、すなわちLogistic(μ, 1)
Logistic(μ, θ)   # 位置がμでスケールがθのロジスティック分布

params(d)       # パラメータを取得、すなわち(μ, θ)
location(d)     # 位置パラメータを取得、すなわちμ
scale(d)        # スケールパラメータを取得、すなわちθ
```

外部リンク

  * [ロジスティック分布 - Wikipedia](http://en.wikipedia.org/wiki/Logistic_distribution)
