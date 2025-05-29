```
exchange(snd,graph::ExchangeGraph) -> Task
```

`snd`のデータを、指向グラフ`graph`に従って送信します。この関数はすぐに戻り、結果を生成するタスクを返し、レイテンシを隠すことができます。`fetch`を使用して待機し、結果を取得します。オブジェクト`snd`と`rcv=fetch(exchange(snd,graph))`はベクトルの配列です。値`snd[i][j]`はノード`graph.snd[i][j]`に送信されます。値`rcv[i][j]`はノード`graph.rcv[i][j]`から受信したものです。

# 例

```jldoctest
julia> using PartitionedArrays

julia> snd_ids = [[3,4],[1,3],[1,4],[2]]
4-element Vector{Vector{Int64}}:
 [3, 4]
 [1, 3]
 [1, 4]
 [2]

julia> graph = ExchangeGraph(snd_ids)
ExchangeGraph{Vector{Vector{Int64}}} with 4 nodes


julia> snd = [[10,10],[20,20],[30,30],[40]]
4-element Vector{Vector{Int64}}:
 [10, 10]
 [20, 20]
 [30, 30]
 [40]

julia> t = exchange(snd,graph);

julia> rcv = fetch(t)
4-element Vector{Vector{Int64}}:
 [20, 30]
 [40]
 [10, 20]
 [10, 30]
```
