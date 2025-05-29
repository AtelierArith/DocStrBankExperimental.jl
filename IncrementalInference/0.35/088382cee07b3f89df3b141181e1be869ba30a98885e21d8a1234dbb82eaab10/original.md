```julia
calcPPE(var; ...)
calcPPE(var, varType; ppeType, solveKey, ppeKey)

```

Get the ParametricPointEstimates–-based on full marginal belief estimates–-of a variable in the distributed factor graph. Calculate new Parametric Point Estimates for a given variable.

DevNotes

  * TODO update for manifold subgroups.
  * TODO standardize after AMP3D

Related

[`getPPE`](@ref), [`setPPE!`](@ref), [`getVariablePPE`](@ref)
