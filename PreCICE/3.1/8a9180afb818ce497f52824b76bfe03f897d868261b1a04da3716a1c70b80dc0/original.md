```
setMeshEdge(meshName::String, firstVertexID::Integer, secondVertexID::Integer)
```

Set mesh edge from vertex IDs, return edge ID. Ignored if preCICE doesn't require connectivity for the mesh.

# Arguments

  * `meshName::String`: Name of the mesh to add the edge to.
  * `firstVertexID::Integer`: ID of the first vertex of the edge.
  * `secondVertexID::Integer`: ID of the second vertex of the edge.

# Notes

Previous calls:

  * Vertices with `firstVertexID` and `secondVertexID` were added to the mesh with `meshName`.
