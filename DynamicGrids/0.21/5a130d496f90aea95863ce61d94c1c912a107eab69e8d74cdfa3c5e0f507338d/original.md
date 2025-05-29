```
inbounds(data::AbstractSimData, I::Tuple) -> Tuple{NTuple{2,Int}, Bool}
inbounds(data::AbstractSimData, I...) -> Tuple{NTuple{2,Int}, Bool}
```

Check grid boundaries for a coordinate before writing in [`SetCellRule`](@ref).

Returns a `Tuple` containing a coordinates `Tuple` and a `Bool` - `true` if the cell is inside the grid bounds, `false` if not.

[`BoundaryCondition`](@ref) of type [`Remove`](@ref) returns the coordinate and `false`  to skip coordinates that boundary outside of the grid.

[`Wrap`](@ref) returns a tuple with the current position or it's wrapped equivalent, and `true` as it is allways in-bounds.
