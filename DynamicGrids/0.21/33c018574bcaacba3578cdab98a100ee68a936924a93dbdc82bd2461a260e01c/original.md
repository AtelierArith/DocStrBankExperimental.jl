```
Layout <: MultiGridRenderer

Layout(layout::Array, renderer::Matrix)
```

Layout allows displaying multiple grids in a block layout, by specifying a layout matrix and a list of [`Image`](@ref)s to be run for each.

# Arguments

  * `layout`: A `Vector` or `Matrix` containing the keys or numbers of grids in the   locations to display them. `nothing`, `missing` or `0` values will be skipped.
  * `renderers`: `Vector/Matrix` of [`Image`](@ref), matching the `layout`.   Can be `nothing` or any other value for grids not in layout.
