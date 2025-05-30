```
Geometric(p)
```

*幾何分布*は、成功率`p`を持つ独立したベルヌーイ試行の列において、最初の成功までの失敗の回数を特徴づけます。

$$
P(X = k) = p (1 - p)^k, \quad \text{for } k = 0, 1, 2, \ldots.
$$

```julia
Geometric()    # 成功率0.5の幾何分布
Geometric(p)   # 成功率pの幾何分布

params(d)      # パラメータを取得、すなわち(p,)
succprob(d)    # 成功率を取得、すなわちp
failprob(d)    # 失敗率を取得、すなわち1 - p
```

外部リンク

  * [Geometric distribution on Wikipedia](http://en.wikipedia.org/wiki/Geometric_distribution)
