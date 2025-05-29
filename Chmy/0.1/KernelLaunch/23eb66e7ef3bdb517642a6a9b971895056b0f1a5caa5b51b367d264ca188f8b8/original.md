```
Launcher(arch, grid; outer_width=nothing)
```

Constructs a `Launcher` object configured based on the input parameters.

## Arguments:

  * `arch`: The associated architecture.
  * `grid`: The grid defining the computational domain.
  * `outer_width`: Optional parameter specifying outer width.

!!! warning
    worksize for the last dimension N takes into account only last outer width W[N], N-1 uses W[N] and W[N-1], N-2 uses W[N], W[N-1], and W[N-2].

