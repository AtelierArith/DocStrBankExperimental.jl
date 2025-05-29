```
p8est_iter_volume_info
```

The information that is available to the user-defined [`p8est_iter_volume_t`](@ref) callback function.

*treeid* gives the index in `p4est`->trees of the tree to which *quad* belongs. *quadid* gives the index of *quad* within *tree*'s quadrants array.

| Field  | Note                                                   |
|:------ |:------------------------------------------------------ |
| quad   | the quadrant of the callback                           |
| quadid | id in *quad*'s tree array (see [`p8est_tree_t`](@ref)) |
| treeid | the tree containing *quad*                             |
