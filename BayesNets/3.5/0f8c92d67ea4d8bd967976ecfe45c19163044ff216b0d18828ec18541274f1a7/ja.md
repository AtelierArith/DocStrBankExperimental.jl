```
bayesian_score(G::DAG, names::Vector{Symbol}, data::DataFrame[, ncategories::Vector{Int}[, prior::DirichletPrior]])
```

グラフ構造 `g` のベイジアンスコアを、`data` のデータを用いて計算します。`names` には、`g` の各頂点に対応するシンボルが含まれており、それは `data` の列名です。`ncategories` は、ベイジアンネットワーク内の各変数が取ることができる値の数のベクトルです。

`data` のすべてのエントリは、0 より大きい整数でなければなりません。
