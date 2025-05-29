```
add_node_data!(dg::D, node_name, node_weight, attribute_name) where {D <: DataGraphUnion}
```

DataGraphオブジェクト内の指定されたノード名に対して重み値を追加します。ユーザーは、指定された重みに対して「属性名」を渡す必要があります。その属性名に対してノード重み値が定義されていない他のすべてのノードは、デフォルトでゼロの値になります。
