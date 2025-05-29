```
(graph,cref)=graph_sid_exp(k;T=Float64)
```

`k` 行列の掛け算に従って指数関数を近似する多項式評価を計算します。係数は論文から直接コピーされています。

評価は degopt フォーマットに埋め込まれており、関数 [`graph_sastre_yks_degopt`](@ref) を使用しています。さらに、`k<=3` の場合は Paterson–Stockmeyer 法を使用します。

**参考文献**

1. J. Sastre, J. Ibáñez, E. Defez. "行列指数関数の計算を強化する". Applied Mathematics of Computation, 340:206-220, 2019. DOI: [10.1016/j.amc.2018.08.017](https://doi.org/10.1016/j.amc.2018.08.017)
