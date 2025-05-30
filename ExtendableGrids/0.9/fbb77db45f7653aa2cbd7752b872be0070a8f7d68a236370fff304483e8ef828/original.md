```julia
veryform(
    grid::ExtendableGrids.ExtendableGrid,
    v,
    _::Type{<:ExtendableGrids.AbstractGridComponent}
) -> Any

```

Default veryform method.

"veryform"  means "verify and/or transform"  and is called to check and possibly transform components to be added to the grid via `setindex!`.

The default method just passes data through.
