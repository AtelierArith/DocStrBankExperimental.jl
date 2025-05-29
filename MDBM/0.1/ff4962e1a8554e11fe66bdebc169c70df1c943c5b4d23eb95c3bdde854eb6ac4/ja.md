```
triangulation(DT1::Array{Tuple{Int64,Int64}})::Array{Tuple{Int64,Int64,Int64}}
```

解法点群に基づく三角形分割（点の三つ組のリストとして）を提供します。DT1は、`connect`によって行われたエッジ接続の結果です。
