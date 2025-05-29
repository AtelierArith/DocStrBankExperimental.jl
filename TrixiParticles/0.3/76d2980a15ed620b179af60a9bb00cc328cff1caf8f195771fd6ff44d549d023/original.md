```
restart_with!(semi, sol)
```

Set the initial coordinates and velocities of all systems in `semi` to the final values in the solution `sol`. [`semidiscretize`](@ref) has to be called again afterwards, or another [`Semidiscretization`](@ref) can be created with the updated systems.

# Arguments

  * `semi`:   The semidiscretization
  * `sol`:    The `ODESolution` returned by `solve` of `OrdinaryDiffEq`
