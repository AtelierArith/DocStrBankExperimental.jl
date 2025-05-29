```
divg_grad(F, K, grid, I...)
```

Compute the divergence of the gradient of a field `F` weighted by a coefficient `K` on a structured grid `grid`. This operation is performed along all dimensions of the grid.

## Arguments

  * `F`: The field whose gradient is to be computed.
  * `K`: The weighting field for the gradient.
  * `grid`: The structured grid on which the operation is performed.
  * `I...`: The indices specifying the location on the grid.
