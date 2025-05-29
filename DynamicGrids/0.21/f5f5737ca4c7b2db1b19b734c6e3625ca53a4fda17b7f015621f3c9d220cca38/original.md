```
SetNeighbors <: SetNeighborhoodRule

SetNeighbors(f, neighborhood=Moor(1))
SetNeighbors{R,W}(f, neighborhood=Moor(1))
```

A [`SetCellRule`](@ref) to manually write to the array with the specified neighborhood. Indexing outside the neighborhood is undefined behaviour.

Function `f` is passed four arguments: a [`SimData`](@ref) object, the specified [`Neighborhood`](@ref) object, the grid state or `Tuple` of grid states for the cell,  and the `Tuple{Int,Int}` index of the current cell.

To update the grid, you can use: [`add!`](@ref), [`sub!`](@ref) for `Number`, and [`and!`](@ref), [`or!`](@ref) for `Bool`. These methods can be safely combined writes from all grid cells.

Directly using `setindex!` is possible, but may cause bugs as multiple cells may write to the same location in an unpredicatble order. As a rule, directly setting a neighborhood index should only be done if it always sets the samevalue - then it can be guaranteed that any writes from othe grid cells reach the same result.

[`neighbors`](@ref), [`offsets`](@ref) and [`positions`](@ref) are useful methods for `SetNeighbors` rules.

## Example

This example adds a value to all neighbors:

```jldoctest
using DynamicGrids

rule = SetNeighbors{:a}() do data, neighborhood, a, I
    add_to_neighbors = your_func(a)
    for pos in positions(neighborhood)
        add!(data[:b], add_to_neighbors, pos...)
    end
end
# output
SetNeighbors{:a,:a}(
    f = var"#1#2"
    neighborhood = Moore{1, 2, 8, Nothing}
)
```
