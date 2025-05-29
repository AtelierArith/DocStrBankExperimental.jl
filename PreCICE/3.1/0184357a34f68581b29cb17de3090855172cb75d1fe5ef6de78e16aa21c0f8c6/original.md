```
setMeshQuads(meshName::String, vertices::AbstractArray{Integer})
```

Set mesh Quad from vertex IDs.

# Arguments

  * `meshName::String`: Name of the mesh to add the Quad to.
  * `vertices::AbstractArray{Integer}`: IDs of the edges of the Quads. It has the shape [N x 4] where N = number of Quads.
