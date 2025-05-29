```
read_inp(file::String)
```

Read Abaqus .inp-file and convert meshes to a point cloud with the help of the [`AbaqusReader.jl`](https://github.com/JuliaFEM/AbaqusReader.jl) package. Every element is converted to a point. The center of the element becomes the position of the point and the element volume becomes the point volume. Element sets defined in Abaqus are converted to corresponding point sets.

Currently supported mesh elements: [:Tet4, :Hex8]

# Arguments

  * `file::String`: Path to Abaqus .inp-file.

# Returns

  * `position::Matrix{Float64}`: Point position (midpoint of every element).
  * `volume::Vector{Float64}`: Point volume (volume of every element).
  * `point_sets`: Element sets defined in the .inp-file.
