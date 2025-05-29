```
p4est_connectivity_new_copy(num_vertices, num_trees, num_corners, vertices, ttv, ttt, ttf, ttc, coff, ctt, ctc)
```

Allocate a connectivity structure and populate from constants. The attribute fields are initialized to NULL.

### Parameters

  * `num_vertices`:[in] Number of total vertices (i.e. geometric points).
  * `num_trees`:[in] Number of trees in the forest.
  * `num_corners`:[in] Number of tree-connecting corners.
  * `coff`:[in] Corner-to-tree offsets (num_corners + 1 values). This must always be non-NULL; in trivial cases it is just a pointer to a p4est_topix value of 0.

### Returns

The connectivity is checked for validity.

### Prototype

```c
p4est_connectivity_t *p4est_connectivity_new_copy (p4est_topidx_t num_vertices, p4est_topidx_t num_trees, p4est_topidx_t num_corners, const double *vertices, const p4est_topidx_t * ttv, const p4est_topidx_t * ttt, const int8_t * ttf, const p4est_topidx_t * ttc, const p4est_topidx_t * coff, const p4est_topidx_t * ctt, const int8_t * ctc);
```
