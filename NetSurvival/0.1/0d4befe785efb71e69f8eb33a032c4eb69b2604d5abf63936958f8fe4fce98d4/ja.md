```
GenPoharPerme
```

このメソッドは、参考文献に記載されているように、(E,P)のためのコピュラを考慮して、一般化ポハールパーミメソッドの下でのネット生存確率を推定します。次のように使用できます：

```
fit(GenPoharPerme(copula), @formula(Surv(time, status)~ x1 + x2), data, ratetable)
```

`GenPoharPerme(::IndependenceCopula)`は単に`PoharPerme`を返すことに注意してください。

参考文献：

  * [Laverny2025](@cite) Laverny, O., Grafféo, N., & Giorgi, R. (2025). 非パラメトリックなネット生存の推定：死因間の依存性の下で。arXivプレプリントarXiv:2502.09273。
