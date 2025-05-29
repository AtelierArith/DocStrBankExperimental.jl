```
add_edge_checked!([f!,], ict::IncrementalCycleTracker, v, w)
```

インクリメンタルサイクルトラッカーである ict を使用して、エッジ `v=>w` を追加すると基盤となるグラフにサイクルが導入されるかどうかを確認します。もしそうであれば、false を返し、ict をそのままにします。そうでなければ、基盤となるグラフを更新し、true を返します。

# オプションの `f!` 引数

デフォルトでは、`add_edge!` 関数が基盤となるグラフを更新するために使用されます。しかし、より複雑なグラフの場合、ユーザーは手動でグラフの更新操作を指定したい場合があります。これは、オプションの `f!` コールバック引数を渡すことで実現できます。このコールバックは、サイクルが検出されない場合に基盤となるグラフに対して呼び出され、提案されたエッジの追加を実現するために基盤となるグラフを変更する必要があります。

# バッチエッジ追加

オプションとして、`v` または `w`（`in_out_reverse` フラグに応じて）は、共通のソースまたはターゲットを共有する頂点のコレクションであり、個別の更新よりも効率的に頂点をバッチ追加することができます。

## 例

```jldoctest
julia> using Graphs

julia> G = SimpleDiGraph(3)
{3, 0} directed simple Int64 graph

julia> ict = IncrementalCycleTracker(G)
BFGT_N cycle tracker on SimpleDiGraph{Int64}(0, [Int64[], Int64[], Int64[]], [Int64[], Int64[], Int64[]])

julia> add_edge_checked!(ict, 1, 2)
true

julia> collect(edges(G))
1-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2

julia> add_edge_checked!(ict, 2, 3)
true

julia> collect(edges(G))
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3

julia> add_edge_checked!(ict, 3, 1) # サイクルを追加しようとしています
false

julia> collect(edges(G))
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3
```
