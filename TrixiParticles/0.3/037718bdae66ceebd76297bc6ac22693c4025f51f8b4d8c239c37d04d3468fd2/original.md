```
trixi2vtk(initial_condition::InitialCondition; output_directory="out",
          prefix="", filename="initial_condition", custom_quantities...)
```

Convert [`InitialCondition`](@ref) data to VTK format.

# Arguments

  * `initial_condition`: [`InitialCondition`](@ref) to be saved.

# Keywords

  * `output_directory="out"`: Output directory path.
  * `prefix=""`:              Prefix for the output file.
  * `filename="coordinates"`: Name of the output file.
  * `custom_quantities...`:   Additional custom quantities to include in the VTK output.

# Returns

  * `file::AbstractString`: Path to the generated VTK file.
