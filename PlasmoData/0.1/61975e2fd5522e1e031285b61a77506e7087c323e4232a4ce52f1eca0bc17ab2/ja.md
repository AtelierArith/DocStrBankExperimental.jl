```
get_ordered_edge_data(dg::D, attribute_list) where {D <: DataGraphUnion}
```

`attribute_list`にある属性の順序付きエッジデータ行列を返します。`DataGraph`の場合、これは`dg.nodes[1]`に接続されているすべてのエッジが最初に順序付けられ、その後に続きます。`DataDiGraph`の場合、これは`dg.nodes[1]`から始まるすべてのエッジが最初に順序付けられ、`length(dg.nodes)`に対してその後に続きます。
