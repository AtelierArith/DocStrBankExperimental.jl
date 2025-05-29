```
p8est_mesh_quadrant_cumulative(p8est_, mesh, cumulative_id, which_tree, quadrant_id)
```

Find a quadrant based on its cumulative number in the local forest. If the quad_to_tree field of the mesh structure exists, this is O(1). Otherwise, we perform a binary search over the processor-local trees.

### Parameters

  * `p8est`:[in] Forest to be worked with.
  * `mesh`:[in] A mesh derived from the forest.
  * `cumulative_id`:[in] Cumulative index over all trees of quadrant. Must refer to a local (non-ghost) quadrant.
  * `which_tree`:[in,out] If not NULL, the input value can be -1 or an initial guess for the quadrant's tree and output is the tree of returned quadrant.
  * `quadrant_id`:[out] If not NULL, the number of quadrant in tree.

### Returns

The identified quadrant.

### Prototype

```c
p8est_quadrant_t *p8est_mesh_quadrant_cumulative (p8est_t * p8est, p8est_mesh_t * mesh, p4est_locidx_t cumulative_id, p4est_topidx_t * which_tree, p4est_locidx_t * quadrant_id);
```
