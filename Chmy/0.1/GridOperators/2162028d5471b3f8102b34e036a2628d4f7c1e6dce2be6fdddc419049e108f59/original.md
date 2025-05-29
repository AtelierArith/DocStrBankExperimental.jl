```
divg(V, ω, grid, I)
```

Compute the divergence of a vector field `V` on a structured grid `grid`, using the mask `ω` to handle masked regions. This operation is performed along all dimensions of the grid.

## Arguments:

  * `V`: The vector field represented as a named tuple of fields.
  * `ω`: The mask for the grid.
  * `grid`: The structured grid on which the operation is performed.
  * `I...`: The indices specifying the location on the grid.
