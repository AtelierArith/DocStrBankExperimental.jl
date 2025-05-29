```
set_indexing_prop!(g, prop)
set_indexing_prop!(g, v, prop, val)
```

Make property `prop` into an indexing property. If any values for this property are already set, each vertex must have unique values. Optionally, set the index `val` for vertex `v`. Any vertices without values will be set to a default ("(prop)(v)").
