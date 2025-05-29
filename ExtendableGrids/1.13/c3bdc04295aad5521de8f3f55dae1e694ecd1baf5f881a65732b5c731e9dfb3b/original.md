```julia
update!(
    grid::ExtendableGrids.ExtendableGrid,
    T::Type{<:ExtendableGrids.AbstractGridComponent}
) -> Any

```

Reinstantiate grid component (only if it exists)
