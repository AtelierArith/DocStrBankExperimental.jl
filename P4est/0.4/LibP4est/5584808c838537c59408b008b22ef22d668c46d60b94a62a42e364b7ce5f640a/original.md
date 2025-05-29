```
p4est_find_quadrant_cumulative(p4est_, cumulative_id, which_tree, quadrant_id)
```

Search a local quadrant by its cumulative number in the forest.

We perform a binary search over the processor-local trees, which means that it is advisable NOT to use this function if possible, and to try to maintain O(1) tree context information in the calling code.

### Parameters

  * `p4est`:[in] Forest to be worked with.
  * `cumulative_id`:[in] Cumulative index over all trees of quadrant.
  * `which_tree`:[in,out] If not NULL, the input value can be -1 or an initial guess for the quadrant's tree. An initial guess must be the index of a nonempty local tree. Output is the tree of returned quadrant.
  * `quadrant_id`:[out] If not NULL, the number of quadrant in tree.

### Returns

The identified quadrant.

### Prototype

```c
p4est_quadrant_t *p4est_find_quadrant_cumulative (p4est_t * p4est, p4est_locidx_t cumulative_id, p4est_topidx_t * which_tree, p4est_locidx_t * quadrant_id);
```
