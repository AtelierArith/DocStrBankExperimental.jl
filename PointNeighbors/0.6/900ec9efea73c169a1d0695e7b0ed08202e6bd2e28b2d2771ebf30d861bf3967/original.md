```
FullGridCellList(; min_corner, max_corner, search_radius = 0.0,
                 periodicity = false, backend = DynamicVectorOfVectors{Int32},
                 max_points_per_cell = 100)
```

A simple cell list implementation where each (empty or non-empty) cell of a rectangular (axis-aligned) domain is assigned a list of points. This cell list only works when all points are inside the specified domain at all times.

Only set `min_corner` and `max_corner` and use the default values for the other arguments to create an empty "template" cell list that can be used to create an empty "template" neighborhood search. See [`copy_neighborhood_search`](@ref) for more details.

# Keywords

  * `min_corner`: Coordinates of the domain corner in negative coordinate directions.
  * `max_corner`: Coordinates of the domain corner in positive coordinate directions.
  * `search_radius = 0.0`: Search radius of the neighborhood search, which will determine the                        cell size. Use the default of `0.0` to create a template (see above).
  * `periodicity = false`: Set to `true` when using a [`PeriodicBox`](@ref) with the                        neighborhood search. When using [`copy_neighborhood_search`](@ref),                        this option can be ignored an will be set automatically depending                        on the periodicity of the neighborhood search.
  * `backend = DynamicVectorOfVectors{Int32}`: Type of the data structure to store the actual   cell lists. Can be

      * `Vector{Vector{Int32}}`: Scattered memory, but very memory-efficient.
      * `DynamicVectorOfVectors{Int32}`: Contiguous memory, optimizing cache-hits.
  * `max_points_per_cell = 100`: Maximum number of points per cell. This will be used to                              allocate the `DynamicVectorOfVectors`. It is not used with                              the `Vector{Vector{Int32}}` backend.
