```
p4est_quadrant_exists(p4est_, ghost, treeid, q, exists_arr, rproc_arr, rquad_arr)
```

Checks if quadrant exists in the local forest or the ghost layer.

For quadrants across tree corners it checks if the quadrant exists in any of the corner neighbors, thus it can execute multiple queries.

### Parameters

  * `p4est`:[in] The forest in which to search for *q*
  * `ghost`:[in] The ghost layer in which to search for *q*
  * `treeid`:[in] The tree to which *q* belongs (can be extended).
  * `q`:[in] The quadrant that is being searched for.
  * `exists_arr`:[in,out] Must exist and be of of elem_size = sizeof (int) for inter-tree corner cases. Is resized by this function to one entry for each corner search and set to true/false depending on its existence in the local forest or ghost_layer.
  * `rproc_arr`:[in,out] If not NULL is filled with one rank per query.
  * `rquad_arr`:[in,out] If not NULL is filled with one quadrant per query. Its piggy3 member is defined as well.

### Returns

true if the quadrant exists in the local forest or in the ghost_layer, and false if doesn't exist in either.

### Prototype

```c
int p4est_quadrant_exists (p4est_t * p4est, p4est_ghost_t * ghost, p4est_topidx_t treeid, const p4est_quadrant_t * q, sc_array_t * exists_arr, sc_array_t * rproc_arr, sc_array_t * rquad_arr);
```
