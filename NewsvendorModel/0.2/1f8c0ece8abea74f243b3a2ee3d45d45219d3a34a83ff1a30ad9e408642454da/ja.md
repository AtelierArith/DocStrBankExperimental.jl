```
q_scarf(anp::AbstractNewsvendorProblem)
```

最小期待利益を最大化する数量を計算します。すべての分布が同じ平均と分散を持つ場合の最悪ケースの解（Scarf, 1958）

$$
q_{scarf} = \mu + \sigma/2 * (\sqrt{r} - \sqrt{1/r})
$$

ここで

$$
r = \frac{\textrm{不足コスト}}{ \textrm{過剰コスト}}
$$
