```
t8_forest_tree_get_leaves(forest, ltree_id)
```

Return the array of leaf elements of a local tree in a forest.

# Arguments

  * `forest`:[in] The forest.
  * `ltree_id`:[in] The local id of a local tree of *forest*.

# Returns

An array of [`t8_element_t`](@ref) * storing all leaf elements of this tree.

### Prototype

```c
t8_element_array_t * t8_forest_tree_get_leaves (const t8_forest_t forest, const t8_locidx_t ltree_id);
```
