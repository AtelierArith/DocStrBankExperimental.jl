```
t8_forest_element_neighbor_eclass(forest, ltreeid, elem, face)
```

Return the eclass of the tree in which a face neighbor of a given element lies.

# Arguments

  * `forest.`:[in] A committed forest.
  * `ltreeid.`:[in] The local tree in which the element lies.
  * `elem.`:[in] An element in the tree *ltreeid*.
  * `face.`:[in] A face number of *elem*.

# Returns

The local tree id of the tree in which the face neighbor of *elem* across *face* lies.

### Prototype

```c
t8_eclass_t t8_forest_element_neighbor_eclass (t8_forest_t forest, t8_locidx_t ltreeid, const t8_element_t *elem, int face);
```
