```
t8_cmesh_set_tree_vertices(cmesh, gtree_id, vertices, num_vertices)
```

Set the vertex coordinates of a tree in the cmesh. This is currently inefficient, since the vertices are duplicated for each tree. Eventually this function will be replaced by a more efficient one. It is not allowed to call this function after t8*cmesh*commit. The eclass of the tree has to be set before calling this function.

# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `gtree_id`:[in] The global number of the tree.
  * `vertices`:[in] An array of 3 doubles per tree vertex.
  * `num_vertices`:[in] The number of verticess in *vertices*. Must match the number of corners of the tree.

### Prototype

```c
void t8_cmesh_set_tree_vertices (t8_cmesh_t cmesh, const t8_gloidx_t gtree_id, const double *vertices, const int num_vertices);
```
