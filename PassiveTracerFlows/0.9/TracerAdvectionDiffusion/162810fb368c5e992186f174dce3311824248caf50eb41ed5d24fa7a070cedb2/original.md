```
struct ThreeDAdvectingFlow <: AbstractAdvectingFlow
```

A container for the advecting flow of a three dimensional `TracerAdvectionDiffusion.Problem`. Includes:

  * `u::Function`: function for the $x$-component of the advecting flow
  * `v::Function`: function for the $y$-component of the advecting flow
  * `w::Function`: function for the $z$-component of the advecting flow
  * `steadyflow::Bool`: boolean declaring whether or not the flow is steady (i.e., not time dependent)
