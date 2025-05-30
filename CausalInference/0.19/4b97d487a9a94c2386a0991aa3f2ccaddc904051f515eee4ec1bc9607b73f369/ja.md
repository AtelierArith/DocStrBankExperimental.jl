```
graph_to_text(g::AbstractGraph, node_labels::AbstractVector{<:AbstractString}=[]; edge_styles::AbstractDict=Dict())
```

グラフ `g` をノードラベルでラベル付けされたエッジのテーブルとして出力します。

# 引数

  * `g::AbstractGraph`: 出力するグラフ
  * `node_labels::AbstractVector{<:AbstractString}=[]`: ノードのラベル（`g` のノードのインデックスと同じ順序）
  * `edge_styles::AbstractDict=Dict()`: エッジスタイルの辞書（例: `Dict((1, 2) => "->", (2, 3) => "<->")`）

# 例

```
g = DiGraph(4)
for (i, j) in [(1, 2), (2, 3), (2, 4)]
    add_edge!(g, i, j)
end
graph_to_text(g)
```
