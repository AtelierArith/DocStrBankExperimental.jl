```
t8_forest_get_element_in_tree(forest, ltreeid, leid_in_tree)
```

Return an element of a local tree in a forest.

!!! note
    If the tree id is know, this function should be preferred over t8*forest*get_element. *forest* must be committed before calling this function.


# Arguments

  * `forest`:[in] The forest.
  * `ltreeid`:[in] An id of a local tree in the forest.
  * `leid_in_tree`:[in] The index of an element in the tree.

# Returns

A pointer to the element.

### Prototype

```c
const t8_element_t * t8_forest_get_element_in_tree (t8_forest_t forest, t8_locidx_t ltreeid, t8_locidx_t leid_in_tree);
```
