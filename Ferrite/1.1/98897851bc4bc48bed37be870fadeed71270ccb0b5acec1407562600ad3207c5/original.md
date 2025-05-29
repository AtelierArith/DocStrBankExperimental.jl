```
L2Projector(ip::Interpolation, grid::AbstractGrid; [qr_lhs], [set])
```

A quick way to initiate an `L2Projector`, add an interpolation `ip` on the `set` to it, and then `close!` it so that it can be used to `project`. The optional keyword argument `set` defaults to all cells in the `grid`, while `qr_lhs` defaults to a quadrature rule that integrates the mass matrix exactly for the interpolation `ip`.
