```
t8_cmesh_get_tree_vertices(cmesh, ltreeid)
```

Return a pointer to the vertex coordinates of a tree.

# Arguments

  * `cmesh`:[in] The cmesh.
  * `ltreeid`:[in] The id of a local tree.

# Returns

If stored, a pointer to the vertex coordinates of *tree*. If no coordinates for this tree are found, NULL.

### Prototype

```c
double * t8_cmesh_get_tree_vertices (t8_cmesh_t cmesh, t8_locidx_t ltreeid);
```
