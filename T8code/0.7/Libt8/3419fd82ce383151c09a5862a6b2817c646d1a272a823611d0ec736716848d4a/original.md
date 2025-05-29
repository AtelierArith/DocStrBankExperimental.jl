```
t8_forest_get_tree_vertices(forest, ltreeid)
```

Return a pointer to the vertex coordinates of a tree.

# Arguments

  * `forest`:[in] The forest.
  * `ltreeid`:[in] The id of a local tree.

# Returns

If stored, a pointer to the vertex coordinates of *tree*. If no coordinates for this tree are found, NULL.

### Prototype

```c
double * t8_forest_get_tree_vertices (t8_forest_t forest, t8_locidx_t ltreeid);
```
