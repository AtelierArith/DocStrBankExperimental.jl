```
p8est_connectivity_new_copy(num_vertices, num_trees, num_edges, num_corners, vertices, ttv, ttt, ttf, tte, eoff, ett, ete, ttc, coff, ctt, ctc)
```

Allocate a connectivity structure and populate from constants. The attribute fields are initialized to NULL.

### Parameters

  * `num_vertices`:[in] Number of total vertices (i.e. geometric points).
  * `num_trees`:[in] Number of trees in the forest.
  * `num_edges`:[in] Number of tree-connecting edges.
  * `num_corners`:[in] Number of tree-connecting corners.
  * `eoff`:[in] Edge-to-tree offsets (num_edges + 1 values). This must always be non-NULL; in trivial cases it is just a pointer to a p4est_topix value of 0.
  * `coff`:[in] Corner-to-tree offsets (num_corners + 1 values). This must always be non-NULL; in trivial cases it is just a pointer to a p4est_topix value of 0.

### Returns

The connectivity is checked for validity.

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_new_copy (p4est_topidx_t num_vertices, p4est_topidx_t num_trees, p4est_topidx_t num_edges, p4est_topidx_t num_corners, const double *vertices, const p4est_topidx_t * ttv, const p4est_topidx_t * ttt, const int8_t * ttf, const p4est_topidx_t * tte, const p4est_topidx_t * eoff, const p4est_topidx_t * ett, const int8_t * ete, const p4est_topidx_t * ttc, const p4est_topidx_t * coff, const p4est_topidx_t * ctt, const int8_t * ctc);
```
