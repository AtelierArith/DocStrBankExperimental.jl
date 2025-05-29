```
p6est_tree_get_vertices(conn, which_tree, vertices)
```

Get the vertices of the corners of a tree.

### Parameters

  * `conn`:[in] the 2D+1D connectivity structure
  * `which_tree`:[in] a tree in the forest
  * `vertices`:[out] the coordinates of the corners of the tree

### Prototype

```c
void p6est_tree_get_vertices (p6est_connectivity_t * conn, p4est_topidx_t which_tree, double vertices[24]);
```
