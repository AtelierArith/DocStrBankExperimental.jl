```
run_EC_on_edges(dg, threshold_range; attribute = dg.edge_data.attributes[1], scale = false)
```

グラフのエッジを `threshold_range` の各値でフィルタリングし、各フィルタリング後にオイラー特性を計算することによって、オイラー特性曲線を返します。 `attribute` が定義されていない場合、デフォルトで DataGraph の `EdgeData` の最初の属性になります。 `scale` はブール値で、元のグラフのオブジェクトの総数（ノード + エッジ）でオイラー特性をスケーリングするかどうかを示します。
