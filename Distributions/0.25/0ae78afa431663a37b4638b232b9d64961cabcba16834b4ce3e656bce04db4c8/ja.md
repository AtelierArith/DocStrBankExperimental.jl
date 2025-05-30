```
Binomial(n,p)
```

*二項分布*は、一連の独立した試行における成功の数を特徴づけます。これは2つのパラメータを持ちます：`n`は試行の数、`p`は個々の試行における成功の確率であり、分布は次のようになります：

$$
P(X = k) = {n \choose k}p^k(1-p)^{n-k},  \quad \text{ for } k = 0,1,2, \ldots, n.
$$

```julia
Binomial()      # n = 1 および p = 0.5 の二項分布
Binomial(n)     # n 試行の二項分布、成功率 p = 0.5
Binomial(n, p)  # n 試行の二項分布、成功率 p

params(d)       # パラメータを取得、すなわち (n, p)
ntrials(d)      # 試行の数を取得、すなわち n
succprob(d)     # 成功率を取得、すなわち p
failprob(d)     # 失敗率を取得、すなわち 1 - p
```

外部リンク：

  * [Wikipediaの二項分布](http://en.wikipedia.org/wiki/Binomial_distribution)
