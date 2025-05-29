```
p8est_iterate_ext(p8est_, ghost_layer, user_data, iter_volume, iter_face, iter_edge, iter_corner, remote)
```

[`p8est_iterate_ext`](@ref) adds the option *remote*: if this is false, then it is the same as [`p8est_iterate`](@ref); if this is true, then corner/edge callbacks are also called on corners/edges for hanging faces/edges touched by local quadrants.

### Prototype

```c
void p8est_iterate_ext (p8est_t * p8est, p8est_ghost_t * ghost_layer, void *user_data, p8est_iter_volume_t iter_volume, p8est_iter_face_t iter_face, p8est_iter_edge_t iter_edge, p8est_iter_corner_t iter_corner, int remote);
```
