```
t8_forest_get_coarse_tree(forest, ltreeid)
```

Given the local id of a tree in a forest, return the coarse tree of the cmesh that corresponds to this tree.

# Arguments

  * `forest`:[in] The forest.
  * `ltreeid`:[in] The local id of a tree in the forest.

# Returns

The coarse tree that matches the forest tree with local id *ltreeid*.

### Prototype

```c
t8_ctree_t t8_forest_get_coarse_tree (t8_forest_t forest, t8_locidx_t ltreeid);
```
