```
add_graph_data!(dg::D, weight, attribute) where {D <: DataGraphUnion}
```

値 `weight` を属性名の下でグラフに追加します。属性がすでに定義されている場合、その値は `weight` にリセットされます。
