信頼区間の幅を特定の `p` 値で計算します。これは、次の論文に基づいています：Carvalho (2011), "Confidence intervals for the minimum of a function using extreme value statistics"

これは、最適化された関数の最小値に対する信頼区間の現在の推定値が、確率 $(1-p)$ で次の区間内にあることを意味します。

```
] l1 - w, l1 [
```

サンプルされた関数点の数が無限大に近づくとき、ここで

```
w = width_of_confidence_interval(a, p)
l1 = best_fitness(a)
```
