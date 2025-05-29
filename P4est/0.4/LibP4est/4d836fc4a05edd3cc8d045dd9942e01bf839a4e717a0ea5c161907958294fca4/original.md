```
p4est_iterate_ext(p4est_, ghost_layer, user_data, iter_volume, iter_face, iter_corner, remote)
```

[`p4est_iterate_ext`](@ref) adds the option *remote*: if this is false, then it is the same as [`p4est_iterate`](@ref); if this is true, then corner callbacks are also called on corners for hanging faces touched by local quadrants.

### Prototype

```c
void p4est_iterate_ext (p4est_t * p4est, p4est_ghost_t * ghost_layer, void *user_data, p4est_iter_volume_t iter_volume, p4est_iter_face_t iter_face, p4est_iter_corner_t iter_corner, int remote);
```
