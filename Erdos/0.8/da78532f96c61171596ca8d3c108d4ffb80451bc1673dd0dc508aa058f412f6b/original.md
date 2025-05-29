```
rem_vertices!(g, vs)
rem_vertices!(g, v1, v2, ....)
```

Remove the vertices in `vs` from graph `g`.

Some vertices of `g` may be reindexed during the removal. To keep track of the reindexing, a vertex map is returned, associating vertices with changed indexes to their old indexes.
