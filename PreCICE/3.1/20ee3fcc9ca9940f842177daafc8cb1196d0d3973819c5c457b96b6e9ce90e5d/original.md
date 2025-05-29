```
    readData(meshName::String, dataName::String, valueIndices::AbstractArray{Cint}, relativeReadTime::Float64)
```

Reads values of specified vertices from data of a mesh. Values are read into a matrix in the order specified by vertices.

The 1D/Scalar-format of values is a vector of length N. The 2D-format of values is [N x 2]. The 3D-format of values is [N x 3]. Where N is the number of vertices.

The data is read at relativeReadTime, which indicates the point in time measured from the beginning of the current time step. `relativeReadTime = 0` corresponds to data at the beginning of the time step. Assuming that the user will call `advance(dt)` at the end of the time step, `dt` indicates the size of the current time step. Then `relativeReadTime = dt` corresponds to the data at the end of the time step.

# Arguments

  * `meshName::String`: Name of the mesh to read the data from.
  * `dataName::String`: Name of the data to be read from
  * `valueIndices::AbstractArray{Cint}`: The vertex ids of the vertices to read data from.
  * `relativeReadTime::Float64`: The point in time relative to the beginning of the current time step to read the data from.

# Returns

  * `values::AbstractArray{Float64}`: The values read from preCICE. Shape [N x D] where N = number of vertices and D = number of data dimensions.

# Notes

  * Every VertexID in vertices is a return value of setMeshVertex or setMeshVertices
  * `size(values) == (length(valueIndices), getDataDimensions(meshName, dataName))`
