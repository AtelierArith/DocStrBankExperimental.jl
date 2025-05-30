```
VonMises(μ, κ)
```

*ボン・ミーゼス分布*は、平均`μ`と集中度`κ`を持ち、確率密度関数は次のようになります。

$$
f(x; \mu, \kappa) = \frac{1}{2 \pi I_0(\kappa)} \exp \left( \kappa \cos (x - \mu) \right)
$$

```julia
VonMises()       # 平均0、集中度1のボン・ミーゼス分布
VonMises(κ)      # 平均0、集中度κのボン・ミーゼス分布
VonMises(μ, κ)   # 平均μ、集中度κのボン・ミーゼス分布
```

外部リンク

  * [ボン・ミーゼス分布 - Wikipedia](http://en.wikipedia.org/wiki/Von_Mises_distribution)
