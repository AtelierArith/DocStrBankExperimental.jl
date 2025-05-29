```
p8est_iter_edge_side
```

| Field       | Note                                                                                                           |
|:----------- |:-------------------------------------------------------------------------------------------------------------- |
| treeid      | the tree on this side                                                                                          |
| edge        | which quadrant side the edge touches                                                                           |
| orientation | the orientation of each quadrant relative to this edge, as in the definition of [`p8est_connectivity_t`](@ref) |
| is_hanging  | boolean: one full quad (0) or two smaller quads (1)                                                            |
