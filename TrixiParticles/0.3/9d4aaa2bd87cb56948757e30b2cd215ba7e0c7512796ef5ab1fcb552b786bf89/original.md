```
trixi2vtk(coordinates; output_directory="out", prefix="", filename="coordinates",
          custom_quantities...)
```

Convert coordinate data to VTK format.

# Arguments

  * `coordinates`: Coordinates to be saved.

# Keywords

  * `output_directory="out"`: Output directory path.
  * `prefix=""`:              Prefix for the output file.
  * `filename="coordinates"`: Name of the output file.
  * `custom_quantities...`:   Additional custom quantities to include in the VTK output.

# Returns

  * `file::AbstractString`: Path to the generated VTK file.
