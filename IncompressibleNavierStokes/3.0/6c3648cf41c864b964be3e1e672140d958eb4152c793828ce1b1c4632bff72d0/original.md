```julia
create_right_hand_side(
    setup,
    psolver
) -> IncompressibleNavierStokes.var"#right_hand_side#331"

```

```
create_right_hand_side(setup, psolver)
```

Creates a function that computes the right-hand side of the Navier-Stokes equations for a given setup and pressure solver.

# Arguments

  * `setup`: The simulation setup containing grid and boundary conditions.
  * `psolver`: The pressure solver to be used.

# Returns

A function that computes the right-hand side of the Navier-Stokes equations.
