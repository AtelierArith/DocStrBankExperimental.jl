```
SetCell <: SetCellRule

SetCell(f)
SetCell{R,W}(f)
```

A [`SetCellRule`](@ref) to manually write to the array where you need to. `f` is passed a [`AbstractSimData`](@ref) object, the grid state or `Tuple` of grid  states for the cell and a `Tuple{Int,Int}` index of the current cell.

To update the grid, you can use: [`add!`](@ref), [`sub!`](@ref) for `Number`, and [`and!`](@ref), [`or!`](@ref) for `Bool`. These methods safely combined writes from all grid cells - directly using `setindex!` would cause bugs.

## Example

Choose a destination cell and if it is in the grid, update it based on the  state of both grids:

```jldoctest SetCell
using DynamicGrids
rule = SetCell{Tuple{:a,:b},:b}() do data, (a, b), I 
    dest = your_dest_pos_func(I)
    if isinbounds(data, dest)
        destval = your_dest_val_func(a, b)
        add!(data[:b], destval, dest...)
    end
end

# output
SetCell{Tuple{:a, :b},:b}(
    f = var"#1#2"
)
```
