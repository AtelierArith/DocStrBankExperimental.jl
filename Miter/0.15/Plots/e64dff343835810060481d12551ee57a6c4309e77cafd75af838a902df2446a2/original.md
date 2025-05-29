```julia
Tableau(contents; horizontal_divisions, vertical_divisions)

```

Make a *tableau*, an arrangement of plots on a matrix-like grid. Visually, the arrangement corresponds to how Julia would display a matrix: rows are rendered as rows, columns as columns.

See [`balanced_matrix`](@ref) for arranging a vector.

Axes are not aligned automatically, use [`sync_bounds`](@ref).

# Divisions

FIXME explain how the divisions syntax works

# Supported API

`contents` are exposed via the array interface as a matrix.

You can merge `Tableau`s with `hcat`, `vcat`, and `hvcat` (`[...; ...]`).
