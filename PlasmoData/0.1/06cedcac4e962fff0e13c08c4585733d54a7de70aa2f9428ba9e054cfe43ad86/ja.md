```
add_node_dataset!(dg::D, node_list, weight_list, attribute) where {D <: DataGraphUnion}
```

`weight_list`のノードデータを`dg`に追加します。`node_list`は`dg`内のノードのリストであり、`weight_list`は`attribute`という名前の下にノードデータとして保存される値/物のリストです。`node_list`と`weight_list`は同じ長さでなければならず、`weight_list`のエントリは`node_list`内の対応するノードに追加されます。
