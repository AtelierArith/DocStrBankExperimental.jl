```
t8_cmesh_get_tree_geom_hash(cmesh, gtreeid)
```

Get the hash of the geometry stored for a tree in a cmesh.

# Arguments

  * `cmesh`:[in] A committed cmesh.
  * `gtreeid`:[in] A global tree in *cmesh*.

# Returns

The hash of the tree's geometry or if only one geometry exists, its hash.

### Prototype

```c
size_t t8_cmesh_get_tree_geom_hash (t8_cmesh_t cmesh, t8_gloidx_t gtreeid);
```
