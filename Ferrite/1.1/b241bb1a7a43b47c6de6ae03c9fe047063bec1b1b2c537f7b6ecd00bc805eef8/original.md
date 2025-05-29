```
create_coloring(g::Grid, cellset=1:getncells(g); alg::ColoringAlgorithm)
```

Create a coloring of the cells in grid `g` such that no neighboring cells have the same color. If only a subset of cells should be colored, the cells to color can be specified by `cellset`.

Returns a vector of vectors with cell indexes, e.g.:

```julia
ret = [
   [1, 3, 5, 10, ...], # cells for color 1
   [2, 4, 6, 12, ...], # cells for color 2
]
```

Two different algorithms are available, specified with the `alg` keyword argument:

  * `alg = ColoringAlgorithm.WorkStream` (default): Three step algorithm from Turcksin et al. [Turcksin2016](@cite), albeit with a greedy coloring in the second step. Generally results in more colors than `ColoringAlgorithm.Greedy`, however the cells are more equally distributed among the colors.
  * `alg = ColoringAlgorithm.Greedy`: greedy algorithm that works well for structured quadrilateral grids such as e.g. quadrilateral grids from `generate_grid`.

The resulting colors can be visualized using [`Ferrite.write_cell_colors`](@ref).

!!! note "Cell to color mapping"
    In a previous version of Ferrite this function returned a dictionary mapping cell ID to color numbers as the first argument. If you need this mapping you can create it using the following construct:

    ```julia
    colors = create_coloring(...)
    cell_colormap = Dict{Int,Int}(
        cellid => color for (color, cellids) in enumerate(final_colors) for cellid in cellids
    )
    ```


# References

  * [Turcksin2016](@cite) Turcksin et al. ACM Trans. Math. Softw. 43 (2016).
