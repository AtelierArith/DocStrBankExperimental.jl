```
get_cell_idxs(longlats, cell_geom::Vector; threshold = 1000) -> cell_idxs

get_cell_idxs(longs, lats, cell_geom::Vector; threshold = 1000) -> cell_idxs
```

与えられた各経度と緯度に対して、`cell_geom`内の最も近いセルのインデックスを返します。`cell_geom`内のポイントから`threshold`メートル以内にグリッドセルがない場合は、インデックス0を返します。`cell_geom`は、元のジオメトリ（`Box`として表現）または経度緯度ジオメトリ（`Quadrangle`として表現）である可能性があります。
