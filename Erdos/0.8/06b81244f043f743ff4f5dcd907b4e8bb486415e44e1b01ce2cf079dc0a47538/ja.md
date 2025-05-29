```
stochastic_block_model(c::Matrix{Float64}, n::Vector{Int}; seed::Int = -1)
stochastic_block_model(cin::Float64, coff::Float64, n::Vector{Int}; seed::Int = -1)
```

確率ブロックモデル（SBM）に従って生成されたグラフを返します。

`c[a,b]` : ブロック `a` に属する頂点のブロック `b` に対する平均隣接数。上三角部分のみが考慮されます。下三角部分は $c[b,a] = c[a,b] * n[a]/n[b]$ によって決定されます。 `n[a]` : ブロック `a` の頂点数

2 番目の形式は、`c[a,a]=cin` および `c[a,b]=coff` を持つ SBM からサンプリングします。

SBM の動的バージョンについては、`StochasticBlockModel` 型および関連関数を参照してください。
