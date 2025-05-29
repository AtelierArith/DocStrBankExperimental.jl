```
set_prop!(g, val)
set_prop!(g, v, val)
set_prop!(g, e, val)
set_prop!(g, s, d, val)
```

Set (replace) the specific property (data for vertices, ids for edges, max id for the graph) with value `val` in graph `g`, vertex `v`, or edge `e` (optionally referenced by source vertex `s` and destination vertex `d`). Will return false if vertex or edge does not exist, true otherwise.
