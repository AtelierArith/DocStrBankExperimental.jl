```
t8_forest_global_tree_id(forest, ltreeid)
```

Return the global id of a local tree or a ghost tree.

# Arguments

  * `forest`:[in] The forest.
  * `ltreeid`:[in] An id 0 <= *ltreeid* < num_local_trees + num_ghosts specifying a local tree or ghost tree.

# Returns

The global id corresponding to the tree with local id *ltreeid*. *forest* must be committed before calling this function.

# See also

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing for more details about tree indexing.

### Prototype

```c
t8_gloidx_t t8_forest_global_tree_id (const t8_forest_t forest, const t8_locidx_t ltreeid);
```
