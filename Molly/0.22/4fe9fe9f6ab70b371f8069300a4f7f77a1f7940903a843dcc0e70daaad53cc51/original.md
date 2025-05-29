```
VirialLogger(n_steps)
VirialLogger(T, n_steps)
```

Log the [`virial`](@ref) of a system throughout a simulation.

This should only be used on systems containing just pairwise interactions, or where the specific interactions, general interactions and constraints do not contribute to the virial.
