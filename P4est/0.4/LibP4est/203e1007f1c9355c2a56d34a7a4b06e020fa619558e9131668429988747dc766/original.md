```
p4est_mesh_get_neighbors(p4est_, ghost, mesh, curr_quad_id, direction, neighboring_quads, neighboring_encs, neighboring_qids)
```

Lookup neighboring quads of quadrant in a specific direction.

### Parameters

  * `p4est`:[in] Forest to be worked with.
  * `ghost`:[in] Ghost layer.
  * `mesh`:[in] Mesh structure.
  * `curr_quad_id`:[in] Process-local id of current quad.
  * `direction`:[in] Direction i in which to look for adjacent quadrants is encoded as follows: 0 .. 3 neighbor(-s) across face i, 4 .. 7 neighbor(-s) across corner i-4. TODO: Allow any combination of empty output arrays.
  * `neighboring_quads`:[out] Array containing neighboring quad(-s). Needs to be empty on input, size of [`p4est_quadrant_t`](@ref) *. May be NULL, then **neighboring_qids** must not be NULL.
  * `neighboring_qids`:[out] Array containing quadrant ids for neighboring quadrants. May be NULL, then no neighboring qids are collected. If non-NULL the array needs to be empty and will contain int. CAUTION: Note, that the encodings differ from the encodings saved in the mesh. TODO: Encodings are the same as in p4est_mesh for all quadrants. TODO: Ghosts can be encoded by returning the quad_to_quad convention in qid. For ghost quadrants, we add -300 to the values in p4est_mesh. This means that values below -100 belong to ghosts, values above to locals. Positive values are for local quadrants, negative values indicate ghost quadrants. Faces: 1 .. 8 => same size neighbor (r * 4 + nf) + 1; nf = 0 .. 3 face index; r = 0 .. 1 relative orientation 9 .. 24 => double size neighbor 9 + h * 8 + r * 4 + nf; h = 0 .. 1 number of the subface; r, nf as above 25 .. 32 => half-size neighbors 25 + r * 4 + nf; r, nf as above Corners: 1 .. 4 => size not encoded for corners nc + 1; nc = 0 .. 3 corner index
  * `neighboring_encs`:[out] Array containing encodings for neighboring quads. Needs to be empty, contains int.

### Prototype

```c
p4est_locidx_t p4est_mesh_get_neighbors (p4est_t * p4est, p4est_ghost_t * ghost, p4est_mesh_t * mesh, p4est_locidx_t curr_quad_id, p4est_locidx_t direction, sc_array_t * neighboring_quads, sc_array_t * neighboring_encs, sc_array_t * neighboring_qids);
```
