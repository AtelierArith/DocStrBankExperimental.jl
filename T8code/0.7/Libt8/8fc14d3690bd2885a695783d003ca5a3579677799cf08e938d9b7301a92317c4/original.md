```
t8_forest_leaf_face_orientation(forest, ltreeid, ts, leaf, face)
```

Compute the leaf face orientation at given face in a forest.

For more information about the encoding of face orientation refer to t8*cmesh*get*face*neighbor.

# Arguments

  * `forest`:[in] The forest. Must have a valid ghost layer.
  * `ltreeid`:[in] A local tree id.
  * `ts`:[in] The eclass scheme of the element.
  * `leaf`:[in] A leaf in tree *ltreeid* of *forest*.
  * `face`:[in] The index of the face across which the face neighbors are searched.

# Returns

Face orientation encoded as integer.

### Prototype

```c
int t8_forest_leaf_face_orientation (t8_forest_t forest, const t8_locidx_t ltreeid, const t8_eclass_scheme_c *ts, const t8_element_t *leaf, int face);
```
