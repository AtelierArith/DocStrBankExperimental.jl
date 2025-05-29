```julia
resetTreeCliquesForUpSolve!(treel)

```

Reset the Bayes (Junction) tree so that a new upsolve can be performed.

Notes

  * Will change previous clique status from `DOWNSOLVED` to `INITIALIZED` only.
  * Sets the color of tree clique to `lightgreen`.
