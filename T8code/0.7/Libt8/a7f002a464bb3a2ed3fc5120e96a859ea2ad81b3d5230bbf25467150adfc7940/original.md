```
t8_cmesh_set_join_by_stash(cmesh, connectivity, do_both_directions)
```

Sets the face connectivity information of an un-committed  based on the cmesh stash.

!!! warning
    This routine might be too expensive for very large meshes. In this case, consider to use a fully featured mesh generator.


!!! note
    This routine does not detect periodic boundaries.


# Arguments

  * `cmesh`:[in,out] An uncommitted cmesh. The trees eclasses and vertices do need to be set.
  * `connectivity`:[in,out] If connectivity is not NULL the variable is filled with a pointer to an allocated face connectivity array. The ownership of this array goes to the caller. This argument is mainly used for debugging and testing purposes. The dimension of *connectivity* are  [ntrees,[`T8_ECLASS_MAX_FACES`](@ref),3]. For each element and each face the following is stored: neighbor_tree_id, neighbor_dual_face_id, orientation
  * `do_both_directions`:[in] Compute the connectivity from both neighboring sides. Takes much longer to compute.

### Prototype

```c
void t8_cmesh_set_join_by_stash (t8_cmesh_t cmesh, int **connectivity, const int do_both_directions);
```
