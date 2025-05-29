```
symmetry(N::AbstractUnipartiteNetwork)
```

s^inとs^out（ユニパーティネットワークの入出力加重次数）間の対称性を計算します。これはs^inとs^outの間のピアソン相関として計算されます。したがって、-1から1の間の値であり、高い正の値は、多くの出力次数を持つ種が多くの入力次数を持つ傾向があることを示し、負の値はその逆を意味します。無向ネットワークは完全に対称ですが、例えば捕食者が獲物になる可能性が低い食物網は負の対称性を持つでしょう。

> Goa, J., Barzael, B. and Barabási 2016. Universal resilience patterns in complex networks. Nature 530(7590), 307-312. doi:10.1038/nature16948

