```
t8_forest_leaf_face_neighbors(forest, ltreeid, leaf, pneighbor_leaves, face, dual_faces, num_neighbors, pelement_indices, pneigh_scheme, forest_is_balanced)
```

Compute the leaf face neighbors of a forest.

!!! note
    If there are no face neighbors, then *neighbor_leaves = NULL, num_neighbors = 0, and *pelement_indices = NULL on output.


!!! note
    Currently *forest* must be balanced.


!!! note
    *forest* must be committed before calling this function.


!!! note
    Important! This routine allocates memory which must be freed. Do it like this:


if (num_neighbors > 0) { eclass_scheme->[`t8_element_destroy`](@ref) (num_neighbors, neighbors); [`T8_FREE`](@ref) (pneighbor_leaves); [`T8_FREE`](@ref) (pelement_indices); [`T8_FREE`](@ref) (dual_faces); }

# Arguments

  * `forest`:[in] The forest. Must have a valid ghost layer.
  * `ltreeid`:[in] A local tree id.
  * `leaf`:[in] A leaf in tree *ltreeid* of *forest*.
  * `pneighbor_leaves`:[out] Unallocated on input. On output the neighbor leaves are stored here.
  * `face`:[in] The index of the face across which the face neighbors are searched.
  * `dual_faces`:[out] On output the face id's of the neighboring elements' faces.
  * `num_neighbors`:[out] On output the number of neighbor leaves.
  * `pelement_indices`:[out] Unallocated on input. On output the element indices of the neighbor leaves are stored here. 0, 1, ... num_local_el - 1 for local leaves and num_local_el , ... , num_local_el + num_ghosts - 1 for ghosts.
  * `pneigh_scheme`:[out] On output the eclass scheme of the neighbor elements.
  * `forest_is_balanced`:[in] True if we know that *forest* is balanced, false otherwise.

### Prototype

```c
void t8_forest_leaf_face_neighbors (t8_forest_t forest, t8_locidx_t ltreeid, const t8_element_t *leaf, t8_element_t **pneighbor_leaves[], int face, int *dual_faces[], int *num_neighbors, t8_locidx_t **pelement_indices, t8_eclass_scheme_c **pneigh_scheme, int forest_is_balanced);
```
