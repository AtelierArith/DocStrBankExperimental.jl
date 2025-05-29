```
divg_grad(F, K, ω, grid, I...)
```

Compute the divergence of the diffusion flux of a field `F` weighted by a coefficient `K` on a structured grid `grid`. This operation is performed along all dimensions of the grid.

## Arguments

  * `F`: The field whose gradient is to be computed.
  * `K`: The weighting field for the gradient.
  * `ω`: The mask for the grid.
  * `grid`: The structured grid on which the operation is performed.
  * `I...`: The indices specifying the location on the grid.
