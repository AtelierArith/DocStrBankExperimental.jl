```
osm_subgraph(g::OSMGraph{U, T, W},
             vertex_list::Vector{U}
             )::OSMGraph where {U <: DEFAULT_OSM_INDEX_TYPE, T <: DEFAULT_OSM_ID_TYPE, W <: Real}
```

指定された頂点を含む別のOSMGraphの部分グラフを表すOSMGraphを作成します。結果として得られるOSMGraphオブジェクトは、指定された頂点（ノード）がメンバーであるすべてのウェイからの頂点も含みます。元のグラフオブジェクト内の頂点番号は部分グラフにマッピングされません。
