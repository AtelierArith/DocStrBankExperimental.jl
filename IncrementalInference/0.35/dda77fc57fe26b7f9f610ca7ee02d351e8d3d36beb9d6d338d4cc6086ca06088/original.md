```julia
ensureSolvable!(dfg; solvableTarget, solvableFallback)

```

Ensure that no variables set as `solvable=1` are floating free without any connected `solvable=1` factors.  If any found, then set those 'free' variable's `solvable=solvableFallback` (default `0`).

Related

[`initAll!`](@ref)
