```
PointIterator(ph::PointEvalHandler)
```

Create an iterator over the points in the [`PointEvalHandler`](@ref). The elements of the iterator are either a [`PointLocation`](@ref), if the corresponding point could be found in the grid, or `nothing`, if the point was not found.

A `PointLocation` can be used to query the cell ID with the `cellid` function, and can be used to reinitialize [`PointValues`](@ref) with [`reinit!`](@ref).

# Examples

```julia
ph = PointEvalHandler(grid, points)

for point in PointIterator(ph)
    point === nothing && continue # Skip any points that weren't found
    reinit!(pointvalues, point)   # Update pointvalues
    # ...
end
```
