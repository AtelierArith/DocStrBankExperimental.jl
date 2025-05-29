```
setMeshTetrahedron(meshName::String, firstEdgeID::Integer, secondEdgeID::Integer, thirdEdgeID::Integer, fourthEdgeID::Integer)
```

Set mesh Tetrahedron from edge IDs.

# Arguments

  * `meshName::String`: Name of the mesh to add the Tetrahedron to.
  * `firstEdgeID::Integer`: ID of the first edge of the Tetrahedron.
  * `secondEdgeID::Integer`: ID of the second edge of the Tetrahedron.
  * `thirdEdgeID::Integer`: ID of the third edge of the Tetrahedron.
  * `fourthEdgeID::Integer`: ID of the fourth edge of the Tetrahedron.

# Notes

Previous calls:

  * Edges with `first_edge_id`, `second_edge_id`, `third_edge_id`, and `fourth_edge_id` were added  to the mesh with the ID `mesh_id`
