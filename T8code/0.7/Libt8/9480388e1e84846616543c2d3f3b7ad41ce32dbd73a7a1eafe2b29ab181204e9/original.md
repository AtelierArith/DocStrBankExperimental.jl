```
t8_forest_get_local_id(forest, gtreeid)
```

Given a global tree id compute the forest local id of this tree. If the tree is a local tree, then the local id is between 0 and the number of local trees. If the tree is not a local tree, a negative number is returned.

# Arguments

  * `forest`:[in] The forest.
  * `gtreeid`:[in] The global id of a tree.

# Returns

The tree's local id in *forest*, if it is a local tree. A negative number if not.

# See also

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing for more details about tree indexing.

### Prototype

```c
t8_locidx_t t8_forest_get_local_id (const t8_forest_t forest, const t8_gloidx_t gtreeid);
```
