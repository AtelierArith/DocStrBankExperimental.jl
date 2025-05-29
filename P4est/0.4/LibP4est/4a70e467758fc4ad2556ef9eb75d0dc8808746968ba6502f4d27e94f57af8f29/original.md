```
p4est_mesh_face_neighbor_init2(mfn, p4est_, ghost, mesh, which_tree, quadrant_id)
```

Initialize a mesh neighbor iterator by quadrant index.

### Parameters

  * `mfn`:[out] A [`p4est_mesh_face_neighbor_t`](@ref) to be initialized.
  * `which_tree`:[in] Tree of quadrant whose neighbors are looped over.
  * `quadrant_id`:[in] Index relative to which_tree of quadrant.

### Prototype

```c
void p4est_mesh_face_neighbor_init2 (p4est_mesh_face_neighbor_t * mfn, p4est_t * p4est, p4est_ghost_t * ghost, p4est_mesh_t * mesh, p4est_topidx_t which_tree, p4est_locidx_t quadrant_id);
```
