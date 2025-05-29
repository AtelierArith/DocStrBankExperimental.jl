```
p8est_mesh_face_neighbor_next(mfn, ntree, nquad, nface, nrank)
```

Move the iterator forward to loop around neighbors of the quadrant.

### Parameters

  * `mfn`:[in,out] Internal status of the iterator.
  * `ntree`:[out] If not NULL, the tree number of the neighbor.
  * `nquad`:[out] If not NULL, the quadrant number within tree. For ghosts instead the number in ghost layer.
  * `nface`:[out] If not NULL, neighbor's face as in [`p8est_mesh_t`](@ref).
  * `nrank`:[out] If not NULL, the owner process of the neighbor.

### Returns

Either a real quadrant or one from the ghost layer. Returns NULL when the iterator is done.

### Prototype

```c
p8est_quadrant_t *p8est_mesh_face_neighbor_next (p8est_mesh_face_neighbor_t * mfn, p4est_topidx_t * ntree, p4est_locidx_t * nquad, int *nface, int *nrank);
```
