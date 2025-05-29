```
get_prop(g)
get_prop(g, v)
get_prop(g, e)
get_prop(g, s, d)
```

Return the specific property (data for vertices, ids for edges, max id for the graph) defined for graph `g`, vertex `v`, or edge `e` (optionally referenced by source vertex `s` and destination vertex `d`). If property does not exist, return an empty collection.
