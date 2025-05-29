```
split_catenation(graph::PeriodicGraph{N}) where N
```

入力 `graph` の連結成分であるタプル `(subgraph, vmaps, mat, dim)` のリストを返します。ここで `subgraph` は入力 `graph` の連結成分です。`vmaps` の各サブリストは、グラフの頂点を対応する `subgraph` の頂点にマッピングする異なるマッピングです。すべての `vmaps` におけるすべての頂点の和集合は、対応する周期性で繰り返され、入力グラフのすべての頂点を重複なく正確にカバーします。`dim` はこれらの連結成分の [`dimensionality`](@ref) であり、`mat` は入力セルと成分のセルとの間の変換行列です。

各サブリストには、同じ頂点インデックスを共有する連結成分が含まれています。

## 例

```jldoctest
julia> g = PeriodicGraph("2    1 1  3 0   1 1  0 1   2 3  1 0   3 2  1 0");

julia> dimensionality(g)
Dict{Int64, Vector{Tuple{Vector{Int64}, Int64}}} with 2 entries:
  2 => [([1], 3)]
  1 => [([2, 3], 2)]

julia> splits = split_catenation(g);

julia> last.(splits) # 一つの2次元カテネーション（頂点1）、一つの1次元（頂点2と3）
2-element Vector{Int64}:
 2
 1

julia> subgraph, vmaps, mat, dim = last(splits);  # 1次元の連結成分

julia> vmaps  # 最初のサブリストは参照ユニットセルから頂点2を取り、2番目は頂点3を取ります。
2-element Vector{PeriodicGraphs.OffsetVertexIterator{2}}:
 [(2, (0,0)), (3, (-1,0))]
 [(2, (1,0)), (3, (0,0))]

julia> subgraph  # サブグラフは関連する2つの頂点のみで構成されています
PeriodicGraph2D(2, PeriodicEdge2D[(1, 2, (0,0)), (1, 2, (1,0))])

julia> mat  # 新しいセルは初期のものの2倍の大きさです
2×2 SMatrix{2, 2, Int64, 4} with indices SOneTo(2)×SOneTo(2):
 2  0
 0  1
```
