```
PerfectEliminationOrder(elimination_algorithm=CliqueTrees.MCS())
```

[`AbstractOrder`](@ref) のインスタンスで、基になるグラフが [chordal](https://en.wikipedia.org/wiki/Chordal_graph) の場合に完璧な排除順序を計算します。非コーダルグラフの場合、最適でない順序を計算します。

`elimination_algorithm` は `CliqueTrees.EliminationAlgorithm` のインスタンスでなければなりません。

!!! warning
    この順序は対称または双方向の彩色問題にのみ適用できます。さらに、その理論的保証は置換による圧縮にのみ適用されます。


!!! danger
    この順序はパッケージ拡張として実装されており、[CliqueTrees.jl](https://github.com/AlgebraicJulia/CliqueTrees.jl) をロードする必要があります。


# 参考文献

  * [Simple Linear-Time Algorithms to Test Chordality of Graphs, Test Acyclicity of Hypergraphs, and Selectively Reduce Acyclic Hypergraphs](https://epubs.siam.org/doi/10.1137/0213035), Tarjan and Yannakakis (1984)
