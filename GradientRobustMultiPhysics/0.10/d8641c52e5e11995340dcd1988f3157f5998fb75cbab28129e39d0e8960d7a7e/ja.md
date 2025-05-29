```
function displace_mesh!(xgrid::ExtendableGrid, source::FEVectorBlock; magnify = 1)
```

グリッドのすべてのノードを、ソース内の変位フィールド（ベクトル値有限要素を期待）に倍率値を掛けて加算することによって移動します。
