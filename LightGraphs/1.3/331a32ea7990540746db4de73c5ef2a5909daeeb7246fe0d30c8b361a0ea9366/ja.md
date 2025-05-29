```
has_path(g::AbstractGraph, u, v; exclude_vertices=Vector())
```

`u`から`v`へのパスが`g`に存在する場合は`true`を返します（`exclude_vertices`に含まれる頂点を避ける場合）または`u == v`の場合。`u`または`v`が`excluded_vertices`に含まれている場合、またはそのようなパスが存在しない場合は`false`を返します。
