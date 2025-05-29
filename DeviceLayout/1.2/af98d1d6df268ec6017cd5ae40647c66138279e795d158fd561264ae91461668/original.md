```
render!(cell::Cell{S}, cs::GeometryStructure;
    memoized_cells=Dict{CoordinateSystem, Cell}(),
    map_meta = identity,
    kwargs...) where {S}
```

Render a geometry structure (e.g., `CoordinateSystem`) to a cell.

Passes each element and its metadata (mapped by `map_meta` if a method is supplied) to `render!(::Cell, element, ::Meta)`, traversing the references such that if a CoordinateSystem is referred to in multiple places, it will become a single cell referred to in multiple places.

Rendering a `GeometryEntity` to a `Cell` uses the optional keyword arguments

  * `map_meta`, a function that takes a `Meta` object and returns another `Meta` object (or `nothing`, in which case rendering is skipped)

Usage note: calling this function with non-empty dictionary `memoized_cells = Dict{CoordinateSystem, Cell}(cs => cell)` is effectively a manual override that forces `cs` to render as `cell`.
