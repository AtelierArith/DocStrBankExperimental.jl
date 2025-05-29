```julia
writeVTK(
    filename::String,
    grid::ExtendableGrids.ExtendableGrid{Tc, Ti};
    append,
    compress,
    kwargs...
) -> Vector{String}

```

exports grid and optional provided data as a vtk file

  * `filename`: filename of the exported file
  * `grid`: grid

Each '(key, value)' pair adds another data entry to the vtk file via WriteVTK functionality.

For the arguments 'append' and 'compress', see documentation of vtk_grid of WriteVTK.
