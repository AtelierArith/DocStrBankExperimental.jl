```
GraphAutomaton(n::Int)
```

`n` 状態 1, 2, ..., `n` を持つ `GraphAutomaton` を作成します。オートマトンは遷移なしで初期化されます。遷移を追加するには [`add_transition!`](@ref) を使用してください。

## 例

ノード 1, 2 を持ち、ラベル 1 の自己ループ、ラベル 2 の状態 1 から状態 2 への遷移、ラベル 3 の状態 2 から状態 1 への遷移を持つオートマトンを作成するには、次のようにします。

```jldoctest
julia> a = GraphAutomaton(2);

julia> add_transition!(a, 1, 1, 1) # 状態 1 のラベル 1 の自己ループを追加
HybridSystems.GraphTransition{Graphs.SimpleGraphs.SimpleEdge{Int64}}(Edge 1 => 1, 1)

julia> add_transition!(a, 2, 2, 1) # 状態 2 のラベル 1 の自己ループを追加
HybridSystems.GraphTransition{Graphs.SimpleGraphs.SimpleEdge{Int64}}(Edge 2 => 2, 2)

julia> add_transition!(a, 1, 2, 2) # 状態 1 から状態 2 へのラベル 2 の遷移を追加
HybridSystems.GraphTransition{Graphs.SimpleGraphs.SimpleEdge{Int64}}(Edge 1 => 2, 3)

julia> add_transition!(a, 2, 1, 3) # 状態 2 から状態 1 へのラベル 3 の遷移を追加
HybridSystems.GraphTransition{Graphs.SimpleGraphs.SimpleEdge{Int64}}(Edge 2 => 1, 4)
```
