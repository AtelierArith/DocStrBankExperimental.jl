```
setMeshTetrahedra(meshName::String, vertices::AbstractArray{Integer})
```

Set mesh Tetrahedron from vertex IDs.

# Arguments

  * `meshName::String`: Name of the mesh to add the Tetrahedron to.
  * `vertices::AbstractArray{Integer}`: IDs of the edges of the Tetrahedra. It has the shape [N x 4] where N = number of Tetrahedra.
