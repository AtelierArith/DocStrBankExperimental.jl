```
get_node_data(dg::D, attribute_list; nodes = dg.nodes) where {D <: DataGraphUnion}
```

属性リストに定義された順序で属性のノードデータの行列を返します。`nodes`が定義されている場合、`nodes`に定義された順序で対応するデータのサブセットを返します。
