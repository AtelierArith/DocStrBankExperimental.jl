```
p8est_connectivity_new(num_vertices, num_trees, num_edges, num_ett, num_corners, num_ctt)
```

Allocate a connectivity structure. The attribute fields are initialized to NULL.

### Parameters

  * `num_vertices`:[in] Number of total vertices (i.e. geometric points).
  * `num_trees`:[in] Number of trees in the forest.
  * `num_edges`:[in] Number of tree-connecting edges.
  * `num_ett`:[in] Number of total trees in edge_to_tree array.
  * `num_corners`:[in] Number of tree-connecting corners.
  * `num_ctt`:[in] Number of total trees in corner_to_tree array.

### Returns

A connectivity structure with allocated arrays.

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_new (p4est_topidx_t num_vertices, p4est_topidx_t num_trees, p4est_topidx_t num_edges, p4est_topidx_t num_ett, p4est_topidx_t num_corners, p4est_topidx_t num_ctt);
```
