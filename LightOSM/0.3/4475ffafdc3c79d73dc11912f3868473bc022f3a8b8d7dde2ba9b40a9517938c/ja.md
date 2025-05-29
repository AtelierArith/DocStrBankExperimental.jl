```
set_dijkstra_state!(g::OSMGraph, src::Union{Integer,Vecotr{<:Integer}, weights::AbstractMatrix; cost_adjustment::Function=(u, v, parents) -> 0.0)
```

1つまたは複数のsrc頂点のためにダイクストラ親状態を計算して設定します。複数のsrcに対してはスレッドが使用されます。すべての頂点のダイクストラ状態を計算することはO(V² + ElogV)の操作であるため、大きなグラフでの使用には注意が必要です。
