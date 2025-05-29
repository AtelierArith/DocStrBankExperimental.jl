```
has_path(g::AbstractGraph, u, v; exclude_vertices=Vector())
```

`g`内で`u`から`v`へのパスが存在する場合は`true`を返します（`exclude_vertices`内の頂点を避ける）。または`u == v`の場合も`true`を返します。`u`または`v`が`excluded_vertices`に含まれている場合、またはそのようなパスが存在しない場合は`false`を返します。
