This structure holds the 2D inter-tree connectivity information. Identification of arbitrary faces and corners is possible.

The arrays tree_to_* are stored in z ordering. For corners the order wrt. yx is 00 01 10 11. For faces the order is -x +x -y +y. They are allocated [0][0]..[0][3]..[num_trees-1][0]..[num_trees-1][3].

The values for tree_to_face are 0..7 where ttf % 4 gives the face number and ttf / 4 the face orientation code. The orientation is 0 for edges that are aligned in z-order, and 1 for edges that are running opposite in z-order.

It is valid to specify num_vertices as 0. In this case vertices and tree_to_vertex are set to NULL. Otherwise the vertex coordinates are stored in the array vertices as [0][0]..[0][2]..[num_vertices-1][0]..[num_vertices-1][2].

The corners are only stored when they connect trees. In this case tree_to_corner indexes into *ctt_offset*. Otherwise the tree_to_corner entry must be -1 and this corner is ignored. If num_corners == 0, tree_to_corner and corner_to_* arrays are set to NULL.

The arrays corner_to_* store a variable number of entries per corner. For corner c these are at position [ctt_offset[c]]..[ctt_offset[c+1]-1]. Their number for corner c is ctt_offset[c+1] - ctt_offset[c]. The entries encode all trees adjacent to corner c. The size of the corner_to_* arrays is num_ctt = ctt_offset[num_corners].

The *_to_attr arrays may have arbitrary contents defined by the user.
