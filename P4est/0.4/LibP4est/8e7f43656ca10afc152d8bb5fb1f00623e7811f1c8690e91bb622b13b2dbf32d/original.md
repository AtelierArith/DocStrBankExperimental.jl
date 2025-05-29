```
p8est_mesh_get_neighbors(p4est_, ghost, mesh, curr_quad_id, direction, neighboring_quads, neighboring_encs, neighboring_qids)
```

Lookup neighboring quads of quadrant in a specific direction

### Parameters

  * `p4est`:[in] Forest to be worked with.
  * `ghost`:[in] Ghost quadrants.
  * `mesh`:[in] Mesh structure.
  * `curr_quad_id`:[in] Process-local ID of current quad.
  * `direction`:[in] Direction in which to look for adjacent quadrants is encoded as follows: 0 .. 5 neighbor(-s) across f_i, 6 .. 17 neighbor(-s) across e_{i-6} 18 .. 25 neighbor(-s) across c_{i-18}
  * `neighboring_quads`:[out] Array containing neighboring quad(-s) Needs to be empty, contains [`p4est_quadrant_t`](@ref)*. May be NULL, then neighboring_qids must not be NULL.
  * `neighboring_encs`:[out] Array containing encodings for neighboring quads as described below Needs to be empty, contains int. CAUTION: Note, that the encodings differ from the encodings saved in the mesh. Positive values are for local quadrants, negative values indicate ghost quadrants. Faces: 1 .. 24 => same size neighbor (r * 6 + nf) + 1; nf = 0 .. 5 face index; r = 0 .. 3 relative orientation 25 .. 120 => double size neighbor 25 + h * 24 + r * 6 + nf; h = 0 .. 3 number of the subface; r, nf as above 121 .. 144 => half size neighbors 121 + r * 6 + nf; r, nf as above Edges: 1 .. 24 => same size neighbor r * 12 + ne + 1; ne = 0 .. 11 edge index; r = 0 .. 1 relative orientation 25 .. 72 => double size neighbor 25 + h * 24 + r * 12 + ne; h = 0 .. 1 number of the subedge; r, ne as above 73 .. 96 => half size neighbors 73 + r * 12 + ne; r, ne as above Corners: 1 .. 8 => nc + 1; nc = 0 .. 7 corner index
  * `neighboring_qids`:[out] Array containing quadrant ids for neighboring quadrants. May be NULL, then no neighboring qids are collected. If non-NULL the array needs to be empty and will contain int.

### Prototype

```c
p4est_locidx_t p8est_mesh_get_neighbors (p8est_t * p4est, p8est_ghost_t * ghost, p8est_mesh_t * mesh, p4est_locidx_t curr_quad_id, p4est_locidx_t direction, sc_array_t * neighboring_quads, sc_array_t * neighboring_encs, sc_array_t * neighboring_qids);
```
