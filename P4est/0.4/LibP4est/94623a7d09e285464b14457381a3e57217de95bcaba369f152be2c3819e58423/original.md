```
p4est_mesh_face_neighbor_init(mfn, p4est_, ghost, mesh, which_tree, quadrant)
```

Initialize a mesh neighbor iterator by quadrant pointer.

### Parameters

  * `mfn`:[out] A [`p4est_mesh_face_neighbor_t`](@ref) to be initialized.
  * `which_tree`:[in] Tree of quadrant whose neighbors are looped over.
  * `quadrant`:[in] Pointer to quadrant contained in which_tree.

### Prototype

```c
void p4est_mesh_face_neighbor_init (p4est_mesh_face_neighbor_t * mfn, p4est_t * p4est, p4est_ghost_t * ghost, p4est_mesh_t * mesh, p4est_topidx_t which_tree, p4est_quadrant_t * quadrant);
```
