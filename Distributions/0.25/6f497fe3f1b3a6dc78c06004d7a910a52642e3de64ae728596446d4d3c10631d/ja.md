```
NegativeBinomial(r,p)
```

*負の二項分布*は、一連の独立したベルヌーイ試行における`r`回目の成功までの失敗の数を表します。これは、成功の数である`r`と、個々の試行における成功の確率である`p`によってパラメータ化されます。

$$
P(X = k) = {k + r - 1 \choose k} p^r (1 - p)^k, \quad \text{for } k = 0,1,2,\ldots.
$$

分布は任意の正の`r`に対しても明確に定義されており、その場合

$$
P(X = k) = \frac{\Gamma(k+r)}{k! \Gamma(r)} p^r (1 - p)^k, \quad \text{for } k = 0,1,2,\ldots.
$$

```julia
NegativeBinomial()        # r = 1 および p = 0.5 の負の二項分布
NegativeBinomial(r, p)    # r 回の成功と成功率 p の負の二項分布

params(d)       # パラメータを取得、すなわち (r, p)
succprob(d)     # 成功率を取得、すなわち p
failprob(d)     # 失敗率を取得、すなわち 1 - p
```

外部リンク:

  * [Wolframの負の二項分布](https://reference.wolfram.com/language/ref/NegativeBinomialDistribution.html)
