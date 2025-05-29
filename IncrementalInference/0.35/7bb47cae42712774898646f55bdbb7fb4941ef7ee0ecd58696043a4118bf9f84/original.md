```julia
initAll!(dfg; ...)
initAll!(dfg, solveKey; _parametricInit, solvable, N)

```

Perform `graphinit` over all variables with `solvable=1` (default).

See also: [`ensureSolvable!`](@ref), (EXPERIMENTAL 'treeinit')
