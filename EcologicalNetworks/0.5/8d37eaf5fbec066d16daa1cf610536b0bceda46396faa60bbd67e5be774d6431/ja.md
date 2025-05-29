```
heterogeneity(N::AbstractUnipartiteNetwork)
```

単一ネットワークのヘテロジニティを計算します。これは、種間の入出力次数の違いを定量化するトポロジー的特性です。これは、σ*in * σ*out / s_meanとして計算されます。値が0の場合、すべての種が同じ（加重された）入出力次数を持つことを示します。

> Goa, J., Barzael, B. and Barabási 2016. Universal resilience patterns in complex networks. Nature 530(7590), 307-312. doi:10.1038/nature16948

