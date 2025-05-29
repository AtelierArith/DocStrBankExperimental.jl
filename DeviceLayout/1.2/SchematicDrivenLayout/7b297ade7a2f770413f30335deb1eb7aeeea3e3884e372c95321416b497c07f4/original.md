```
function map_metadata(comp::AbstractComponent, map_meta)
```

For every element in `geometry(comp)` with original meta `m`, set its metadata to `map_meta(m)`.

Recursive on referenced structures.
