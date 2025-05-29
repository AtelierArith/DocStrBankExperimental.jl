```
GrapheneRibbon(len, wid[, center; kw...])
```

Construct a graphene ribbon sample with zigzag edges. To get armchair edges, simply rotate the lattice by 90 degrees.

## Arguments

  * `len`: the length of the ribbon.
  * `wid`: the width of the ribbon.
  * `center`: the unit cell coordinates of the bottom-left corner of the ribbon. Default is `(0, 0)`.

All other keyword arguments are passed to `span_unitcells` (see its documentation for details).
