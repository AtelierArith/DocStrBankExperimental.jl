```
    writeData(meshName::String, dataName::String, valueIndices::AbstractArray{Cint}, values::AbstractArray{Float64})
```

Writes values of specified vertices to data of a mesh. Values are provided as a matrix. The order of the provided data follows the order specified by vertices.

The 1D/Scalar-format of values is a vector of length N. The 2D-format of values is [N x 2]. The 3D-format of values is [N x 3]. Where N is the number of vertices.

# Arguments

  * `meshName::String`: Name of the mesh to write the data to.
  * `dataName::String`: Name of the data to be written.
  * `valueIndices::AbstractArray{Cint}`: The vertex ids of the vertices to write data to. Shape [N x 1] where N = number of vertices.
  * `values::AbstractArray{Float64}`: The values to be written to preCICE. Shape [N x D] where N = number of vertices and D = number of data dimensions.

# Notes

Previous calls:

  * Every VertexID in `valueIndices` is return value of setMeshVertex or setMeshVertices
  * `size(values) == (length(valueIndices), getDataDimensions(meshName, dataName))`

See also:

  * [`setMeshVertex`](@ref)
  * [`setMeshVertices`](@ref)
  * [`getDataDimensions`](@ref)
