```
t8_forest_ghost_get_ghost_treeid(forest, gtreeid)
```

Given a global tree compute the ghost local tree id of it.

# Arguments

  * `forest`:[in] The forest. Ghost layer must exist.
  * `gtreeid`:[in] A global tree in *forest*.

# Returns

If *gtreeid* is also a ghost tree, the index in the ghost->ghost_trees array of the tree. Otherwise a negative number. *forest* must be committed before calling this function.

# See also

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing for more details about tree indexing.

### Prototype

```c
t8_locidx_t t8_forest_ghost_get_ghost_treeid (t8_forest_t forest, t8_gloidx_t gtreeid);
```
