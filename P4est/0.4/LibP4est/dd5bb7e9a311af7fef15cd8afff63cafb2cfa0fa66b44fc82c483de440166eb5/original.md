```
p8est_mesh_get_quadrant(p4est_, mesh, qid)
```

Access a process-local quadrant inside a forest. Needs a mesh with populated quad_to_tree array. This is a special case of p8est*mesh*quadrant_cumulative.

### Parameters

  * `p4est`:[in] The forest.
  * `mesh`:[in] The mesh.
  * `qid`:[in] Process-local id of the quadrant (cumulative over trees).

### Returns

A pointer to the requested quadrant.

### Prototype

```c
p8est_quadrant_t *p8est_mesh_get_quadrant (p8est_t * p4est, p8est_mesh_t * mesh, p4est_locidx_t qid);
```
