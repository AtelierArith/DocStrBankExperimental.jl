```
centered(ent::AbstractGeometry; on_pt=zero(Point{T}))
```

Centers a copy of `ent` on `on_pt`, with promoted coordinates if necessary. This function will not throw an `InexactError()`, even if `ent` had integer coordinates.
