```
p4est_mesh_new_ext(p4est_, ghost, compute_tree_index, compute_level_lists, btype)
```

Create a new mesh.

### Parameters

  * `p4est`:[in] A forest that is fully 2:1 balanced.
  * `ghost`:[in] The ghost layer created from the provided `p4est`.
  * `compute_tree_index`:[in] Boolean to decide whether to allocate and compute the quad_to_tree list.
  * `compute_level_lists`:[in] Boolean to decide whether to compute the level lists in quad_level.
  * `btype`:[in] Currently ignored, only face neighbors are stored.

### Returns

A fully allocated mesh structure.

### Prototype

```c
p4est_mesh_t *p4est_mesh_new_ext (p4est_t * p4est, p4est_ghost_t * ghost, int compute_tree_index, int compute_level_lists, p4est_connect_type_t btype);
```
