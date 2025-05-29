```
t8_forest_element_is_leaf(forest, element, local_tree)
```

Query whether a given element is a leaf in a forest.

!!! note
    This does not query for ghost leaves.


!!! note
    *forest* must be committed before calling this function.


# Arguments

  * `forest`:[in] The forest.
  * `element`:[in] An element of a local tree in *forest*.
  * `local_tree`:[in] A local tree id of *forest*.

# Returns

True (non-zero) if and only if *element* is a leaf in *local_tree* of *forest*.

### Prototype

```c
int t8_forest_element_is_leaf (const t8_forest_t forest, const t8_element_t *element, const t8_locidx_t local_tree);
```
