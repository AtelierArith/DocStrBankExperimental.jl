```
get_ordered_edge_data(dg::D, attribute::String) where {D <: DataGraphUnion}
```

`attribute`の順序付きエッジデータベクターを返します。`DataGraph`の場合、これは`dg.nodes[1]`に接続されているすべてのエッジが最初に順序付けられ、その後に続きます。`DataDiGraph`の場合、これは`dg.nodes[1]`から始まるすべてのエッジが最初に順序付けられ、`length(dg.nodes)`に対して同様に続きます。
