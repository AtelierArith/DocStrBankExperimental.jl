```
reset_aggregated_jumps!(integrator, uprev = nothing; update_jump_params=true)
```

Reset the state of jump processes and associated solvers following a change in parameters or such.

Notes     - `update_jump_params=true` will recalculate the rates stored within any       MassActionJump that was built from the parameter vector. If the parameter       vector is unchanged this can safely be set to false to improve performance.
