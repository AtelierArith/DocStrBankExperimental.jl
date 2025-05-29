```
order_edges!(dg) where {D <: DataGraphUnion}
```

`dg`のエッジをその順序に従って配置します。`dg.nodes`の順序に従います。`DataGraph`の場合、これは`dg.nodes[1]`に接続されたすべてのエッジが最初に順序付けられ、その後に続きます。`DataDiGraph`の場合、これは`dg.nodes[1]`から始まるすべてのエッジが最初に順序付けられ、その後`length(dg.nodes)`に従って続きます。
