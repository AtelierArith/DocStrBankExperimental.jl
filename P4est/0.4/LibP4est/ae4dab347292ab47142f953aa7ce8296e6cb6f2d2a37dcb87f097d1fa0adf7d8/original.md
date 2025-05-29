```
p8est_face_quadrant_exists(p8est_, ghost, treeid, q, face, hang, owner_rank)
```

Checks if quadrant exists in the local forest or the ghost layer.

For quadrants across tree boundaries it checks if the quadrant exists across any face, but not across edges or corners.

### Parameters

  * `p8est`:[in] The forest in which to search for *q*.
  * `ghost`:[in] The ghost layer in which to search for *q*.
  * `treeid`:[in] The tree to which *q* belongs.
  * `q`:[in] The quadrant that is being searched for.
  * `face`:[in,out] On input, face id across which *q* was created. On output, the neighbor's face number augmented by orientation, so face is in 0..23.
  * `hang`:[in,out] If not NULL, signals that q is bigger than the quadrant it came from. The child id of that originating quadrant is passed into hang. On output, hang holds the hanging face number of *q* that is in contact with its originator.
  * `owner_rank`:[out] Filled with the rank of the owner if it is found and undefined otherwise.

### Returns

Returns the local number of *q* if the quadrant exists in the local forest or in the ghost_layer. Otherwise, returns -2 for a domain boundary and -1 if not found.

### Prototype

```c
p4est_locidx_t p8est_face_quadrant_exists (p8est_t * p8est, p8est_ghost_t * ghost, p4est_topidx_t treeid, const p8est_quadrant_t * q, int *face, int *hang, int *owner_rank);
```
