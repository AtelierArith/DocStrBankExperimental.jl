```
t8_forest_iterate_faces(forest, ltreeid, element, face, leaf_elements, user_data, tree_lindex_of_first_leaf, callback)
```

### プロトタイプ

```c
void t8_forest_iterate_faces (t8_forest_t forest, t8_locidx_t ltreeid, const t8_element_t *element, int face, t8_element_array_t *leaf_elements, void *user_data, t8_locidx_t tree_lindex_of_first_leaf, t8_forest_iterate_face_fn callback);
```
