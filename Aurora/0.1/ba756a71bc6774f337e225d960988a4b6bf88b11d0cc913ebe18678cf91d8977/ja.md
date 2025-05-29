```
ReplicatedSample(Z::AbstractVector)
```

この型は、同じ分布 $F_i$ から引き出された $K$ 個の独立同分布サンプル $Z_{i1},\dotsc, Z_{iK}$ を表します。この設定は、Aurora が開発されたもので、分布 $F_i$ はその平均 $\mu_i$ によってパラメータ化されます。すなわち、

$$
\mu_i = \mathbb E_{F_i}[ Z_{ij}],
$$

さらに、煩雑なパラメータ $lpha_i$ があり、$F_i = F(\cdot \mid \mu_i, \alpha_i)$ となり、

$$
Z_{i1},\dotsc, Z_{iK} \mid  \mid \mu_i, \alpha_i \; \sim \; F(\cdot \mid \mu_i, \alpha_i).
$$
