```
get_distance(A::Int, B::Int, 
             nodes::Dict{Int,T} , 
             vertices_to_nodes::Vector{Int}) where T<:Union{OpenStreetMapX.ENU,OpenStreetMapX.ECEF}
```

補助関数 - グラフの2つの頂点を取り、それらの間の距離を返します。A*アルゴリズムの直線距離ヒューリスティックを計算するために使用されます。

**引数**

  * `A` : 開始頂点
  * `B` : 終了頂点
  * `nodes` : .osmノードIDと対応するポイント座標の辞書
  * `vertices_to_nodes` : グラフの頂点を.osmファイルのノードにマッピングする辞書
