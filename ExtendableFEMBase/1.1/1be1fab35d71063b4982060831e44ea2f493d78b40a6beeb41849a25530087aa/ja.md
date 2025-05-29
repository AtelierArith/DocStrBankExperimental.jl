```
function displace_mesh(xgrid::ExtendableGrid, source::FEVectorBlock; magnify = 1)
```

指定された xgrid の座標にソースの変位フィールド（ベクトル値有限要素を期待）を加算して、新しいグリッドを返します。magnify 値を掛け算します。
