```
print_output!()
```

Write all subsequent output of the VoronoiFVM package to screen via println().

This is the default.

If enabled in Pluto notebooks, the output is directed to the terminal  widget below a pluto cell. Warnings in addition are sent via logging in order to not miss them.

This behavior can be changed via [`log_output!`](@ref).

For fine-tuning  solver output, see the `verbose` flag in [`SolverControl`](@ref).
