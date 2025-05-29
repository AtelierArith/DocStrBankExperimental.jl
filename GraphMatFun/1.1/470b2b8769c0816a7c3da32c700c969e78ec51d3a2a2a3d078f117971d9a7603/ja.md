```
(graph,cref)=graph_bbc_exp(k;T=Float64)
```

`k` 行列の掛け算に従って指数関数を近似する多項式評価を計算します。係数は論文から直接コピーされています。

評価は `degopt` 形式に埋め込まれており、[`graph_degopt`](@ref) を参照してください。また、`k< 3` の場合、評価はパターソン–ストックマイヤー法を使用しています。

**参考文献**

1. P. Bader, S. Blanes, and F. Casas. "Computing the matrix exponential with an optimized Taylor polynomial approximation". Mathematics, 7(12), 2019. DOI: [10.3390/math7121174](https://doi.org/10.3390/math7121174)
