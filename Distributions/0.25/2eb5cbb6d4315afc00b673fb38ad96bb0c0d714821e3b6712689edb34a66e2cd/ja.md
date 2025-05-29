```
DiscreteUniform(a,b)
```

*離散一様分布*は、`a`と`b`の間の連続した整数の列にわたる一様分布です（両端を含む）。

$$
P(X = k) = 1 / (b - a + 1) \quad \text{for } k = a, a+1, \ldots, b.
$$

```julia
DiscreteUniform(a, b)   # {a, a+1, ..., b} 上の一様分布

params(d)       # パラメータを取得します。すなわち (a, b)
span(d)         # サポートの範囲を取得します。すなわち (b - a + 1)
probval(d)      # 確率値を取得します。すなわち 1 / (b - a + 1)
minimum(d)      # a を返します
maximum(d)      # b を返します
```

外部リンク

  * [Wikipediaの離散一様分布](http://en.wikipedia.org/wiki/Uniform_distribution_(discrete))
