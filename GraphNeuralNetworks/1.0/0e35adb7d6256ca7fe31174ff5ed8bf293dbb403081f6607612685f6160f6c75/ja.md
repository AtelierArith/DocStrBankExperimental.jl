```
HeteroGraphConv(itr; aggr = +)
HeteroGraphConv(pairs...; aggr = +)
```

異種グラフのための畳み込み層です。

`itr` 引数は `pairs` のイテレータで、形式は `edge_t => layer` です。ここで `edge_t` は `(src_node_type, edge_type, dst_node_type)` の形式の3タプルであり、`layer` は同種グラフのための畳み込み層です。

各畳み込みは対応する関係に適用されます。ノードタイプは複数の関係に関与する可能性があるため、単一の畳み込み出力は `aggr` 関数を使用して集約する必要があります。デフォルトは出力を合計することです。

# フォワード引数

  * `g::GNNHeteroGraph`: 入力グラフ。
  * `x::Union{NamedTuple,Dict}`: 入力ノード特徴。キーはノードタイプで、値はノード特徴テンソルです。

# 例

```jldoctest
julia> g = rand_bipartite_heterograph((10, 15), 20)
GNNHeteroGraph:
  num_nodes: Dict(:A => 10, :B => 15)
  num_edges: Dict((:A, :to, :B) => 20, (:B, :to, :A) => 20)

julia> x = (A = rand(Float32, 64, 10), B = rand(Float32, 64, 15));

julia> layer = HeteroGraphConv((:A, :to, :B) => GraphConv(64 => 32, relu),
                               (:B, :to, :A) => GraphConv(64 => 32, relu));

julia> y = layer(g, x); # 出力は名前付きタプルです

julia> size(y.A) == (32, 10) && size(y.B) == (32, 15)
true
```
