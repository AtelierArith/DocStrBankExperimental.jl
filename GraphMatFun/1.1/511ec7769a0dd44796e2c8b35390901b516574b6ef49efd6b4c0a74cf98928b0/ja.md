```
result=eval_graph(
    graph,
    x;
    vals = nothing,
    input = :A,
    output = size(graph.outputs, 1),
    comporder = nothing,
)

値 `x` でグラフを評価します。通常、これはスカラー値または行列です。`x` がベクトルの場合、値は要素ごとに評価されます。

`comporder` は、グラフが計算される順序を指定するノードの `Vector` です。デフォルトでは [`get_topo_order`](@ref) が使用されます。

`output` は、どのノードを出力として考慮するかを指定する `Int` です。出力ノードは `graph.outputs[output]` です。

`vals` は、グラフ内の出力以外の内容を検査するために使用されます。通常、`vals` は `Dict` です。グラフの計算されたノードを含むように変更されます。ノード `X3` を検査したい場合、入力として空の辞書を初期化できます：

```

julia-repl julia > vals = Dict{Symbol,Any}(); julia > eval_graph(graph, A, vals = vals); julia > vals[:X3] ```
