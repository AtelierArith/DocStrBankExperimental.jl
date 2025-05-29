```
function map_metadata(geom::GeometryStructure, map_meta)
```

Create a copy of `geom` and change original metadata `m` to `map_meta(m)` for all elements.

Recursive on the copies of referenced structures.
