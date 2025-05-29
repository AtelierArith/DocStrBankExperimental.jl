```jldoctest
julia> using VTK

julia> points = [(1.0, 2.0), (3.0, 4.0), (5.0, 6.0)]

julia> vtk_file = VTK.File("output.vtk", VTK.VTKPolyData)

julia> vtk_file.points = points

julia> VTK.write(vtk_file)
```
