```
rungrid(mol, density, tkin, cdmol, deltav, transitions; ...)
```

Generate a grid of τ and Tₑₓ values over the set of physical conditions and selected transitions. Most parameters for a `RunDef` run definition can be set as keyword arguments (e.g., β, bg). Arguments can be passed as scalars or collections. Runs will be executed in parallel if Julia was started with multiple threads.

Resulting cubes are indexed with shape `(n, Tₖ, N, δv, j)` for volume density, kinetic temperature, column density, linewidth, and transition number. The transition index number corresponds to the TRANS value in the LAMDA data file or the index number in the output table.
