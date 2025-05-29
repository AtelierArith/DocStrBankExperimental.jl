```
Cell{S,T}(cs::CoordinateSystem, target::LayoutTarget; kwargs...) where {S,T}
Cell{S}(cs::CoordinateSystem, target::LayoutTarget; kwargs...) where {S}
Cell(cs::CoordinateSystem, unit::CoordinateUnits, target::LayoutTarget; kwargs...)
```

Create a new cell and render `cs` to it according to `target`.

See [`LayoutTarget`](@ref) documentation for details.
