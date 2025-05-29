```
struct TwoDAdvectingFlow <: AbstractAdvectingFlow
```

A container for the advecting flow of a two dimensional `TracerAdvectionDiffusion.Problem`. Includes:

  * `u::Function`: function for the $x$-component of the advecting flow
  * `v::Function`: function for the $y$-component of the advecting flow
  * `steadyflow::Bool`: boolean declaring whether or not the flow is steady (i.e., not time dependent)
