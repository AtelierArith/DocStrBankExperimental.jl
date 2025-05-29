```
mutable struct Cell{S<:Coordinate}
```

A cell has a name and contains polygons and references to `CellArray` or `CellReference` objects. It also records the time of its own creation. As currently implemented it mirrors the notion of cells in GDSII files.

To add elements, use `render!`. To add references, use `addref!` or `addarr!`. To add text, use `text!`.
