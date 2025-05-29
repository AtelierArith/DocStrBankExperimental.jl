```julia
struct BoundaryConditions
```

Stores boundary conditions for each face of the simulation box.

# Fields:

  * `xlo`: boundary style of the lower face of the box in dimension x
  * `xhi`: boundary style of the higher face of the box in dimension x
  * `ylo`: boundary style of the lower face of the box in dimension y
  * `yhi`: boundary style of the higher face of the box in dimension y
  * `zlo`: boundary style of the lower face of the box in dimension z
  * `zhi`: boundary style of the higher face of the box in dimension z
