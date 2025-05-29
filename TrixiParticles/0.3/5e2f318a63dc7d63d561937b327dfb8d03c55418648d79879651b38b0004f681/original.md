```
vtk2trixi(file::String)
```

Load VTK file and convert data to an [`InitialCondition`](@ref).

# Arguments

  * `file`: Name of the VTK file to be loaded.

!!! warning "Experimental Implementation"
    This is an experimental feature and may change in any future releases.


# Example

```jldoctest; output = false

# Create a rectangular shape

rectangular = RectangularShape(0.1, (10, 10), (0, 0), density=1.5, velocity=(1.0, -2.0),                                pressure=1000.0)

# Write the `InitialCondition` to a vtk file

trixi2vtk(rectangular; filename="rectangular", output_directory="out")

# Read the vtk file and convert it to `InitialCondition`

ic = vtk2trixi(joinpath("out", "rectangular.vtu"))

# output

┌──────────────────────────────────────────────────────────────────────────────────────────────────┐ │ InitialCondition{Float64}                                                                        │ │ ═════════════════════════                                                                        │ │ #dimensions: ……………………………………………… 2                                                                │ │ #particles: ………………………………………………… 100                                                              │ │ particle spacing: ………………………………… 0.1                                                              │ └──────────────────────────────────────────────────────────────────────────────────────────────────┘
