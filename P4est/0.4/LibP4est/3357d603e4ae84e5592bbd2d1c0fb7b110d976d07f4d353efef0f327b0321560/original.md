```
p8est_mesh_new(p8est_, ghost, btype)
```

Create a p8est_mesh structure. This function does not populate the quad_to_tree and quad_level fields. To populate them, use p8est*mesh*new_ext.

### Parameters

  * `p8est`:[in] A forest that is fully 2:1 balanced.
  * `ghost`:[in] The ghost layer created from the provided `p4est`.
  * `btype`:[in] Determines the highest codimension of neighbors.

### Returns

A fully allocated mesh structure.

### Prototype

```c
p8est_mesh_t *p8est_mesh_new (p8est_t * p8est, p8est_ghost_t * ghost, p8est_connect_type_t btype);
```
