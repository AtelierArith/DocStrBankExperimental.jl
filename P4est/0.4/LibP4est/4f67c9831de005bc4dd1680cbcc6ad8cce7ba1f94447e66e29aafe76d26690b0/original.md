```
p8est_mesh_face_neighbor_init(mfn, p8est_, ghost, mesh, which_tree, quadrant)
```

Initialize a mesh neighbor iterator by quadrant pointer.

### Parameters

  * `mfn`:[out] A [`p8est_mesh_face_neighbor_t`](@ref) to be initialized.
  * `which_tree`:[in] Tree of quadrant whose neighbors are looped over.
  * `quadrant`:[in] Pointer to quadrant contained in which_tree.

### Prototype

```c
void p8est_mesh_face_neighbor_init (p8est_mesh_face_neighbor_t * mfn, p8est_t * p8est, p8est_ghost_t * ghost, p8est_mesh_t * mesh, p4est_topidx_t which_tree, p8est_quadrant_t * quadrant);
```
