```
BernoulliLogit(logitp=0.0)
```

成功率 `p` のロジット `logitp = logit(p) = log(p/(1-p))` でパラメータ化された *ベルヌーイ分布*。

$$
P(X = k) = \begin{cases}
\operatorname{logistic}(-logitp) = \frac{1}{1 + \exp{(logitp)}} & \quad \text{for } k = 0, \\
\operatorname{logistic}(logitp) = \frac{1}{1 + \exp{(-logitp)}} & \quad \text{for } k = 1.
\end{cases}
$$

外部リンク：

  * [ベルヌーイ分布 - Wikipedia](http://en.wikipedia.org/wiki/Bernoulli_distribution)

関連項目 [`Bernoulli`](@ref)
