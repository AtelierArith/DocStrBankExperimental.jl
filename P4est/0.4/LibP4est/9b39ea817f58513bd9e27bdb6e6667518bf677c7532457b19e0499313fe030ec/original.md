```
p4est_mesh_new(p4est_, ghost, btype)
```

Create a p4est_mesh structure. This function does not populate the quad_to_tree and quad_level fields. To populate them, use p4est*mesh*new_ext.

### Parameters

  * `p4est`:[in] A forest that is fully 2:1 balanced.
  * `ghost`:[in] The ghost layer created from the provided `p4est`.
  * `btype`:[in] Determines the highest codimension of neighbors.

### Returns

A fully allocated mesh structure.

### Prototype

```c
p4est_mesh_t *p4est_mesh_new (p4est_t * p4est, p4est_ghost_t * ghost, p4est_connect_type_t btype);
```
