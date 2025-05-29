```
edge_indices(g::FactorGraph, v::FactorGraphVertex)
```

頂点 `v` に接続されたエッジのインデックスへの遅延イテレータを返します。

`edge_indices` の出力はメモリを割り当てず、外部のプロパティ配列を直接インデックスするために使用できます。

# 例

```jldoctest edge_indices
julia> using IndexedFactorGraphs, Test

julia> g = FactorGraph([0 1 1 0;
                        1 0 0 0;
                        0 0 1 1])
FactorGraph{Int64} は 4 つの変数、3 つの因子、および 5 つのエッジを持っています。

julia> edgeprops = randn(ne(g));

julia> indices = (idx(e) for e in outedges(g, variable(3)));

julia> indices_noalloc = edge_indices(g, variable(3));

julia> @assert edgeprops[collect(indices)] == edgeprops[indices_noalloc]

julia> @test_throws ArgumentError edgeprops[indices]
テストに合格しました
      発生: ArgumentError
```
