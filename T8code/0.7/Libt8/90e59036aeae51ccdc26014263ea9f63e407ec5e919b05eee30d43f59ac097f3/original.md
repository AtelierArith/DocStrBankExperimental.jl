```
t8_forest_get_element(forest, lelement_id, ltreeid)
```

Return an element of the forest.

!!! note
    This function performs a binary search. For constant access, use t8*forest*get*element*in_tree *forest* must be committed before calling this function.


# Arguments

  * `forest`:[in] The forest.
  * `lelement_id`:[in] The local id of an element in *forest*.
  * `ltreeid`:[out] If not NULL, on output the local tree id of the tree in which the element lies in.

# Returns

A pointer to the element. NULL if this element does not exist.

### Prototype

```c
t8_element_t * t8_forest_get_element (t8_forest_t forest, t8_locidx_t lelement_id, t8_locidx_t *ltreeid);
```
