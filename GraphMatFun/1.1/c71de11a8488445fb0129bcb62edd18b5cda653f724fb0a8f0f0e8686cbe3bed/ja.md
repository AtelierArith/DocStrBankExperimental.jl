```
(graph,cref)=graph_bbcs_cheb_exp(k;T=Complex{BigFloat})
```

スキューエルミート行列の指数関数を近似する多項式評価を計算し、参照の手順に従って `k` 行列乗算を行います。

`k > 5` の場合、`k = 5` グラフのスケーリングと平方化に頼ります。グラフは degopt 形式であり、[`graph_degopt`](@ref) を参照してください。

**参考文献**

1. P. Bader, S. Blanes, F. Casas, M. Seydaoglu. "An efficient algorithm to compute the exponential of skew-Hermitian matrices for the time integration of the Schrödinger equation". [arXiv:2103.10132 [math.NA]](https://arxiv.org/abs/2103.10132), 2021.
