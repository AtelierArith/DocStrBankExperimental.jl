```
setMeshTriangle(meshName::String, firstEdgeID::Integer, secondEdgeID::Integer, thirdEdgeID::Integer)
```

Set mesh triangle from vertex IDs.

# Arguments

  * `meshName::String`: Name of the mesh to add the edge to.
  * `firstVertexID::Integer`: ID of the first vertex of the edge.
  * `secondVertexID::Integer`: ID of the second vertex of the edge.
  * `thirdVertexID::Integer`: ID of the third edge of the triangle.

# Notes

Previous calls:

  * Edges with `first_edge_id`, `second_edge_id`, and `third_edge_id` were added to the mesh with the name `meshName`
