```
log_output!()
```

Write all subsequent output of the VoronoiFVM package to screen via Julia's  logging methods (using @info or @warn).

This behavior can be changed via [`print_output!`](@ref).

For fine-tuning  solver output, see the `verbose` flag in [`SolverControl`](@ref).
