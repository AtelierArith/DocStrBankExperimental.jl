```julia
getCliqVarSolveOrderUp(cliq)

```

Determine and return order list of variable ids required for minibatch Gibbs iteration inside `cliq`.

Notes

  * Singleton factors (priors and up messages) back of the list
  * least number of associated factor variables earlier in list
  * Same as mcmcIterationIdsOrdered
