```
Bernoulli(p)
```

*ベルヌーイ分布*は成功率`p`によってパラメータ化され、確率`p`で1の値を取り、確率`1-p`で0の値を取ります。

$$
P(X = k) = \begin{cases}
1 - p & \quad \text{for } k = 0, \\
p & \quad \text{for } k = 1.
\end{cases}
$$

```julia
Bernoulli()    # p = 0.5のベルヌーイ分布
Bernoulli(p)   # 成功率pのベルヌーイ分布

params(d)      # パラメータを取得、すなわち(p,)
succprob(d)    # 成功率を取得、すなわちp
failprob(d)    # 失敗率を取得、すなわち1 - p
```

外部リンク:

  * [ベルヌーイ分布 - Wikipedia](http://en.wikipedia.org/wiki/Bernoulli_distribution)
