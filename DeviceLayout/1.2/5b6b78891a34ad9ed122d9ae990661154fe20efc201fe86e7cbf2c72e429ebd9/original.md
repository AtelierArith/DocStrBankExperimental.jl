```
function map_metadata!(geom::GeometryStructure, map_meta)
```

For every element in `geom` with original meta `m`, set its metadata to `map_meta(m)`.

Recursive on referenced structures.
