```
setMeshQuad(meshName::String, firstEdgeID::Integer, secondEdgeID::Integer, thirdEdgeID, fourthEdgeID::Integer)
```

Set mesh Quad from edge IDs.

# Arguments

  * `meshName::String`: Name of the mesh to add the Quad to.
  * `firstVertexID::Integer`: ID of the first edge of the Quad.
  * `secondVertexID::Integer`: ID of the second edge of the Quad.
  * `thirdEdgeID::Integer`: ID of the third edge of the Quad.
  * `fourthEdgeID::Integer`: ID of the fourth edge of the Quad.

# Notes

Previous calls:

  * Edges with `first_edge_id`, `second_edge_id`, `third_edge_id`, and `fourth_edge_id` were added  to the mesh with the ID `mesh_id`
