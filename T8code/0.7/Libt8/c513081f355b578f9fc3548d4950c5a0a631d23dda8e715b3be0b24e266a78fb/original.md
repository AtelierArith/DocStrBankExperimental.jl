```
t8_forest_get_tree_num_elements(forest, ltreeid)
```

Return the number of elements of a tree.

# Arguments

  * `forest`:[in] The forest.
  * `ltreeid`:[in] A local id of a tree.

# Returns

The number of elements in the local tree *ltreeid*.

### Prototype

```c
t8_locidx_t t8_forest_get_tree_num_elements (t8_forest_t forest, t8_locidx_t ltreeid);
```
