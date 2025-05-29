```
add_edge_data!(datagraph, node_name1, node_name2, edge_weight, attribute_name)
add_edge_data!(datagraph, edge, edge_weight, attribute_name)
```

DataGraphオブジェクト内のnode*name1とnode*name2の間のエッジに重み値を追加します。2番目の関数を使用する場合、`edge`は2つのノード名を持つタプルでなければなりません。ユーザーは指定された重みに対して「属性名」を渡す必要があります。その属性名に対してedge_weight値が定義されていない他のすべてのエッジは、デフォルトでゼロの値になります。
