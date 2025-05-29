```
isinbounds(data, I::Tuple) -> Bool
isinbounds(data, I...) -> Bool
```

Check that a coordinate is within the grid, usually in [`SetCellRule`](@ref).

Unlike [`inbounds`](@ref), [`BoundaryCondition`](@ref) status is ignored.
