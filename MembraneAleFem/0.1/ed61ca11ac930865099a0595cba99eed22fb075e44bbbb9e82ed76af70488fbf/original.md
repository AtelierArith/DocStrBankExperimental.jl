```
Motion
```

Types of mesh motion: `instances(Motion)`

  * `STATIC = 1` –> mesh does not move
  * `EUL    = 2` –> Eulerian mesh motion
  * `LAG    = 3` –> Lagrangian mesh motion
  * `ALEV   = 4` –> ALE-viscous mesh motion
  * `ALEVB  = 5` –> ALE-viscous-bending mesh motion

The choice of motion is stored in `Params.motion` variable in [`Params.jl`](@ref man-params), and is relevant both to the specification of boundary conditions in [`Bc.jl`](@ref man-mesh) and the [finite element analysis](@ref man-analysis).
