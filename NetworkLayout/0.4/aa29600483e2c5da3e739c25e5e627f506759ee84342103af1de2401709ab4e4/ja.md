```
Align(inner_layout :: AbstractLayout{2, Ptype}, angle :: Ptype = zero(Ptype))
```

`inner_layout`の頂点位置を整列させ、結果のレイアウトの主軸が**x**軸と`angle`の角度を持つようにします。また、レイアウトの原点を質量中心（平均ノード位置）に自動的にセンタリングします。

二次元の内部レイアウトのみをサポートします。
