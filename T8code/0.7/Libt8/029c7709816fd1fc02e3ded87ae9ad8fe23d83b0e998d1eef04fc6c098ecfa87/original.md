```
t8_cmesh_get_tree_geometry(cmesh, gtreeid)
```

Get the geometry of a tree.

# Arguments

  * `cmesh`:[in] The cmesh.
  * `gtreeid`:[in] The global tree id of the tree for which the geometry should be returned.

# Returns

The geometry of the tree.

### Prototype

```c
const t8_geometry_c * t8_cmesh_get_tree_geometry (t8_cmesh_t cmesh, t8_gloidx_t gtreeid);
```
