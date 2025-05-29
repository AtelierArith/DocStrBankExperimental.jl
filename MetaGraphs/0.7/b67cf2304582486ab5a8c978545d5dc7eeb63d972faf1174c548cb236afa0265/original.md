```
set_props!(g, dict)
set_props!(g, v, dict)
set_props!(g, e, dict)
set_props!(g, s, d, dict)
```

Bulk set (merge) properties contained in `dict` with graph `g`, vertex `v`, or edge `e` (optionally referenced by source vertex `s` and destination vertex `d`). Will return false if vertex or edge does not exist.
