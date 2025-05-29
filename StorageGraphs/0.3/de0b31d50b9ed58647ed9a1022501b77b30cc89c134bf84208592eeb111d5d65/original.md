```
has_prop(g, v, prop)
has_prop(g, e, prop)
has_prop(g, s, d, prop)
```

Return true if the property `prop` belongs to the specific property (data for vertices, ids for dges) for graph `g`, vertex `v`, or edge `e` (optionally referenced by source vertex `s` and destination vertex `d`). For nodes this will check if `prop` is a key of the node, while for edges it will check if `prop` belongs to the id list.
