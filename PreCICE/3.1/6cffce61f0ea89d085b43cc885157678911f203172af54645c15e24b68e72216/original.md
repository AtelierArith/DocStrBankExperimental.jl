```
writeGradientData(meshName::String, dataName::String, valueIndices::AbstractArray{Cint}, gradientValues::AbstractArray{Float64})
```

Write gradient values of specified vertices to data of a mesh.

The format for a 2D problem with 2 vertices is [v1x*dx v1y*dx v1x*dy v1y*dy; v2x*dx v2y*dx v2x*dy v2y*dy] The format for a 3D problem with 2 vertices is [v1x*dx v1y*dx v1z*dx v1x*dy v1y*dy v1z*dy v1x*dz v1y*dz v1z*dz; v2x*dx v2y*dx v2z*dx v2x*dy v2y*dy v2z*dy v2x*dz v2y*dz v2z*dz]

# Arguments

  * `meshName::String`: Name of the mesh to write the data to.
  * `dataName::String`: Name of the data to be written.
  * `valueIndices::AbstractArray{Cint}`: Indices of the vertex.
  * `gradientValues::AbstractArray{Float64}`: The gradient values to write.

# Notes

Previous calls:

  * [`initialize`](@ref)

# Examples

Write gradient values of a vector data for a 2D problem with 2 vertices:

```julia
valueIndices = [1, 2]
gradientValues = [1.0 2.0 3.0 4.0; 5.0 6.0 7.0 8.0]
PreCICE.writeGradientData("MeshOne", "DataOne", valueIndices, gradientValue)
```
