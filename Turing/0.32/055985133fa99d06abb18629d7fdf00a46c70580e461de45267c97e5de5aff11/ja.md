```
BinomialLogit(n, logitp)
```

*ロジットパラメータ化*された*二項分布*は、一連の独立した試行における成功の数を特徴づけます。

それは二つのパラメータを持ちます：`n`は試行の数、`logitp`は個々の試行における成功の確率のロジットであり、分布は次のようになります。

$$
P(X = k) = {n \choose k}{(\text{logistic}(logitp))}^k (1 - \text{logistic}(logitp))^{n-k}, \quad \text{ for } k = 0,1,2, \ldots, n.
$$

参照： [`Binomial`](@ref)
