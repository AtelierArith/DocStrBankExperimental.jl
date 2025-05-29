```
p8est_mesh_face_neighbor_data(mfn, ghost_data)
```

Get the user data for the current face neighbor.

### Parameters

  * `mfn`:[in] Internal status of the iterator.
  * `ghost_data`:[in] Data for the ghost quadrants that has been synchronized with [`p4est_ghost_exchange_data`](@ref).

### Returns

A pointer to the user data for the current neighbor.

### Prototype

```c
void *p8est_mesh_face_neighbor_data (p8est_mesh_face_neighbor_t * mfn, void *ghost_data);
```
