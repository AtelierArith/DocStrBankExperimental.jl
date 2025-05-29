```
CellIterator(grid::Grid, cellset=1:getncells(grid))
CellIterator(dh::AbstractDofHandler, cellset=1:getncells(dh))
```

Create a `CellIterator` to conveniently iterate over all, or a subset, of the cells in a grid. The elements of the iterator are [`CellCache`](@ref)s which are properly `reinit!`ialized. See [`CellCache`](@ref) for more details.

Looping over a `CellIterator`, i.e.:

```julia
for cc in CellIterator(grid, cellset)
    # ...
end
```

is thus simply convenience for the following equivalent snippet:

```julia
cc = CellCache(grid)
for idx in cellset
    reinit!(cc, idx)
    # ...
end
```

!!! warning
    `CellIterator` is stateful and should not be used for things other than `for`-looping (e.g. broadcasting over, or collecting the iterator may yield unexpected results).

