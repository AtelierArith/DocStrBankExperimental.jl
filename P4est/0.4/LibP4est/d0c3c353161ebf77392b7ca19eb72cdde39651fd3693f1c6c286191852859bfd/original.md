```
p8est_iterate(p4est_, ghost_layer, user_data, iter_volume, iter_face, iter_edge, iter_corner)
```

Execute the user-supplied callback functions at every volume, face, edge and corner in the local forest.

The ghost_layer may be NULL. The *user_data* pointer is not touched by [`p8est_iterate`](@ref), but is passed to each of the callbacks. Any of the callback functions may be NULL. The callback functions are interspersed with each other, i.e. some face callbacks will occur between volume callbacks, and some edge callbacks will occur between face callbacks, etc.:

1. volume callbacks occur in the sorted Morton-index order. 2) a face callback is not executed until after the volume callbacks have been executed for the quadrants that share it. 3) an edge callback is not executed until the face callbacks have been executed for all faces that touch the edge. 4) a corner callback is not executed until the edge callbacks have been executed for all edges that touch the corner. 5) it is not always the case that every face callback for a given quadrant is executed before any of the edge or corner callbacks, and it is not always the case that every edge callback for a given quadrant is executed before any of the corner callbacks. 6) callbacks are not executed at faces, edges or corners that only involve ghost quadrants, i.e. that are not adjacent in the local section of the forest.

### Parameters

  * `p4est`:[in] the forest
  * `ghost_layer`:[in] optional: when not given, callbacks at the boundaries of the local partition cannot provide quadrant data about ghost quadrants: missing ([`p8est_quadrant_t`](@ref) *) pointers are set to NULL, missing indices are set to -1.
  * `user_data`:[in,out] optional context to supply to each callback
  * `iter_volume`:[in] callback function for every quadrant's interior
  * `iter_face`:[in] callback function for every face between quadrants
  * `iter_edge`:[in] callback function for every edge between quadrants
  * `iter_corner`:[in] callback function for every corner between quadrants

### Prototype

```c
void p8est_iterate (p8est_t * p4est, p8est_ghost_t * ghost_layer, void *user_data, p8est_iter_volume_t iter_volume, p8est_iter_face_t iter_face, p8est_iter_edge_t iter_edge, p8est_iter_corner_t iter_corner);
```
