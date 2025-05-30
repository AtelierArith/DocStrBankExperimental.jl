```
PoissonBinomial(p)
```

*ポアソン-バイノミアル分布*は、各試行が異なる成功率を持つ独立した試行のシーケンスにおける成功の数を記述します。これは、ベクトル `p`（長さ $K$）によってパラメータ化され、ここで $K$ は試行の総数であり、`p[i]` は `i` 番目の試行の成功確率に対応します。

$$
P(X = k) = \sum\limits_{A\in F_k} \prod\limits_{i\in A} p[i] \prod\limits_{j\in A^c} (1-p[j]), \quad \text{ for } k = 0,1,2,\ldots,K,
$$

ここで $F_k$ は $\{1,2,3,...,K\}$ から選択できる $k$ 個の整数のすべての部分集合の集合です。

```julia
PoissonBinomial(p)   # 成功率ベクトル p を持つポアソンバイノミアル分布

params(d)            # パラメータを取得、すなわち (p,)
succprob(d)          # 成功率のベクトルを取得、すなわち p
failprob(d)          # 失敗率のベクトルを取得、すなわち 1-p
```

外部リンク：

  * [ポアソン-バイノミアル分布 - Wikipedia](http://en.wikipedia.org/wiki/Poisson_binomial_distribution)
