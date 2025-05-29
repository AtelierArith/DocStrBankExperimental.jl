```julia
using VTK

# (x, y, z) coordinates
points = [
    (0.0, 0.0, 0.0),
    (1.0, 0.0, 0.0),
    (0.0, 1.0, 0.0),
    (0.0, 0.0, 1.0)
]

# Create a VTK file
vtk_file = VTKFile("output.vtk")

# Add points to the VTK file
for (x, y, z) in points
    vtk_file.add_point(x, y, z)
end

# Write the VTK file
vtk_file.write()
```
