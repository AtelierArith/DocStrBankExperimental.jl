```
grid = read_cube(filename)
```

Read a .cube file and return a populated `Grid` data structure. It will detect and skip over atomic information if it is present in the file.

# Arguments

  * `filename::AbstractString`: name of .cube file to which we write the grid; this is relative to `rc[:paths][:grids]`
  * `has_units::Bool=true`: flag for function to read units from file header

# Returns

  * `grid::Grid`: A grid data structure
