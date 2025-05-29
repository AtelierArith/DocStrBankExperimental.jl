```
p8est_connectivity
```

This structure holds the 3D inter-tree connectivity information. Identification of arbitrary faces, edges and corners is possible.

The arrays tree_to_* are stored in z ordering. For corners the order wrt. zyx is 000 001 010 011 100 101 110 111. For faces the order is -x +x -y +y -z +z. They are allocated [0][0]..[0][N-1]..[num_trees-1][0]..[num_trees-1][N-1]. where N is 6 for tree and face, 8 for corner, 12 for edge.

The values for tree_to_face are in 0..23 where ttf % 6 gives the face number and ttf / 6 the face orientation code. The orientation is determined as follows. Let my_face and other_face be the two face numbers of the connecting trees in 0..5. Then the first face corner of the lower of my_face and other_face connects to a face corner numbered 0..3 in the higher of my_face and other_face. The face orientation is defined as this number. If my_face == other_face, treating either of both faces as the lower one leads to the same result.

It is valid to specify num_vertices as 0. In this case vertices and tree_to_vertex are set to NULL. Otherwise the vertex coordinates are stored in the array vertices as [0][0]..[0][2]..[num_vertices-1][0]..[num_vertices-1][2].

The edges are only stored when they connect trees. In this case tree_to_edge indexes into *ett_offset*. Otherwise the tree_to_edge entry must be -1 and this edge is ignored. If num_edges == 0, tree_to_edge and edge_to_* arrays are set to NULL.

The arrays edge_to_* store a variable number of entries per edge. For edge e these are at position [ett_offset[e]]..[ett_offset[e+1]-1]. Their number for edge e is ett_offset[e+1] - ett_offset[e]. The entries encode all trees adjacent to edge e. The size of the edge_to_* arrays is num_ett = ett_offset[num_edges]. The edge_to_edge array holds values in 0..23, where the lower 12 indicate one edge orientation and the higher 12 the opposite edge orientation.

The corners are only stored when they connect trees. In this case tree_to_corner indexes into *ctt_offset*. Otherwise the tree_to_corner entry must be -1 and this corner is ignored. If num_corners == 0, tree_to_corner and corner_to_* arrays are set to NULL.

The arrays corner_to_* store a variable number of entries per corner. For corner c these are at position [ctt_offset[c]]..[ctt_offset[c+1]-1]. Their number for corner c is ctt_offset[c+1] - ctt_offset[c]. The entries encode all trees adjacent to corner c. The size of the corner_to_* arrays is num_ctt = ctt_offset[num_corners].

The *_to_attr arrays may have arbitrary contents defined by the user.

| Field            | Note                                                                                |
|:---------------- |:----------------------------------------------------------------------------------- |
| num_vertices     | the number of vertices that define the *embedding* of the forest (not the topology) |
| num_trees        | the number of trees                                                                 |
| num_edges        | the number of edges that help define the topology                                   |
| num_corners      | the number of corners that help define the topology                                 |
| vertices         | an array of size (3 * *num_vertices*)                                               |
| tree_to_vertex   | embed each tree into  `c++ R^3`  for e.g. visualization (see p8est_vtk.h)           |
| tree_attr_bytes  | bytes per tree in tree_to_attr                                                      |
| tree_to_attr     | not touched by `p4est`                                                              |
| tree_to_tree     | (6 * *num_trees*) neighbors across faces                                            |
| tree_to_face     | (6 * *num_trees*) face to face+orientation (see description)                        |
| tree_to_edge     | (12 * *num_trees*) or NULL (see description)                                        |
| ett_offset       | edge to offset in *edge*to*tree* and *edge*to*edge*                                 |
| edge_to_tree     | list of trees that meet at an edge                                                  |
| edge_to_edge     | list of tree-edges+orientations that meet at an edge (see description)              |
| tree_to_corner   | (8 * *num_trees*) or NULL (see description)                                         |
| ctt_offset       | corner to offset in *corner*to*tree* and *corner*to*corner*                         |
| corner_to_tree   | list of trees that meet at a corner                                                 |
| corner_to_corner | list of tree-corners that meet at a corner                                          |
