```
SimpleGraph{T}(nv, ne, edgestream::Channel)
```

Construct a `SimpleGraph{T}` with `nv` vertices and `ne` edges from `edgestream`. Can result in less than `ne` edges if the channel `edgestream` is closed prematurely. Duplicate edges are only counted once. The element type is the type of `nv`.
