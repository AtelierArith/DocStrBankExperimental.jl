```
getMeshVertexIDsAndCoordinates(meshName::String)::Tuple{AbstractArray{Integer}, AbstractArray{Float64}}
```

Iterating over the region of interest defined by bounding boxes and reading the corresponding coordinates omitting the mapping.

# Arguments

  * `meshName::String`: Name of the mesh to get the vertices and IDs for.

# Returns

  * `vertexIDs::AbstractArray{Integer}`: IDs of the vertices.
  * `vertexCoordinates::AbstractArray{Float64}`: Coordinates of the vertices and corresponding data values. Shape [N x D] where N = number of vertices and D = number of data dimensions.
