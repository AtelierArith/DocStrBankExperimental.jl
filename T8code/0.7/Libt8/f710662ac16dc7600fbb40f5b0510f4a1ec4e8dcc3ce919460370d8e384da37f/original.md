```
t8_cmesh_set_join_by_vertices(cmesh, ntrees, eclasses, vertices, connectivity, do_both_directions)
```

Sets the face connectivity information of an un-committed  based on a list of tree vertices.

!!! warning
    This routine might be too expensive for very large meshes. In this case,  consider to use a fully featured mesh generator.


!!! note
    This routine does not detect periodic boundaries.


# Arguments

  * `cmesh`:[in,out] Pointer to a t8code cmesh object. If set to NULL this argument is ignored.
  * `ntrees`:[in] Number of coarse mesh elements resp. trees.
  * `vertices`:[in] List of per element vertices with dimensions [ntrees,[`T8_ECLASS_MAX_CORNERS`](@ref),[`T8_ECLASS_MAX_DIM`](@ref)].
  * `eclasses`:[in] List of element classes of length [ntrees].
  * `connectivity`:[in,out] If connectivity is not NULL the variable is filled with a pointer to an allocated face connectivity array. The ownership of this array goes to the caller. This argument is mainly used for debugging and testing purposes. The dimension of *connectivity* are [ntrees,[`T8_ECLASS_MAX_FACES`](@ref),3]. For each element and each face the following is stored: neighbor_tree_id, neighbor_dual_face_id, orientation
  * `do_both_directions`:[in] Compute the connectivity from both neighboring sides. Takes much longer to compute.

### Prototype

```c
void t8_cmesh_set_join_by_vertices (t8_cmesh_t cmesh, const t8_gloidx_t ntrees, const t8_eclass_t *eclasses, const double *vertices, int **connectivity, const int do_both_directions);
```
