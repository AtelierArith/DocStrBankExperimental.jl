```
t8_geometry_tree_negative_volume(cmesh, gtreeid)
```

Check if a tree has a negative volume

# Arguments

  * `cmesh`:[in] The cmesh to check
  * `gtreeid`:[in] The global id of the tree

# Returns

True if the tree with id gtreeid has a negative volume. False otherwise.

### Prototype

```c
int t8_geometry_tree_negative_volume (const t8_cmesh_t cmesh, const t8_gloidx_t gtreeid);
```
