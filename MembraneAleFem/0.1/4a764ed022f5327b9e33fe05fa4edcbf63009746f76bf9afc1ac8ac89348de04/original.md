```
Neumann
```

Enumerate types of Neumann boundary conditions: `instances(Neumann)`

  * `SHEAR     = 1` –> apply in-plane force/length in the τ direction
  * `STRETCH   = 2` –> apply in-plane force/length in the ν direction
  * `MOMENT    = 3` –> apply boundary moment

Associate finite element calculations are found in [`calc_bdry_element_residual`](@ref)
