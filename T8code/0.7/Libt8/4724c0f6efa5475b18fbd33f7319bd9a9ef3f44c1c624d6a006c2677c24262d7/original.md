```
t8_forest_get_tree_element_offset(forest, ltreeid)
```

Return the element offset of a local tree, that is the number of elements in all trees with smaller local treeid.

!!! note
    *forest* must be committed before calling this function.


# Arguments

  * `forest`:[in] The forest.
  * `ltreeid`:[in] A local id of a tree.

# Returns

The number of leaf elements on all local tree with id < *ltreeid*.

### Prototype

```c
t8_locidx_t t8_forest_get_tree_element_offset (const t8_forest_t forest, const t8_locidx_t ltreeid);
```
