```
t8_cmesh_set_tree_geometry(cmesh, gtreeid, geom)
```

Set the geometry for a tree, thus specify which geometry to use for this tree.

# Arguments

  * `cmesh`:[in] A non-committed cmesh.
  * `gtreeid`:[in] A global tree id in *cmesh*.
  * `geom`:[in] The geometry to use for this tree. See also t8*cmesh*get*tree*geometry

### Prototype

```c
void t8_cmesh_set_tree_geometry (t8_cmesh_t cmesh, t8_gloidx_t gtreeid, const t8_geometry_c *geom);
```
