```julia
right_hand_side!(dudt, u, params_ref, t)

```

```
right_hand_side!(dudt, u, params_ref, t)
```

Computes the right-hand side of the Navier-Stokes equations in-place.

# Arguments

  * `dudt`: The array to store the computed right-hand side.
  * `u`: The current velocity field.
  * `params_ref`: A reference to the parameters containing the setup and pressure solver.
  * `t`: The current time.

# Returns

Nothing. The result is stored in `dudt`.
