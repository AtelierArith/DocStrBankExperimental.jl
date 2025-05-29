```
SpheroidDiskCell
```

A growing and motile dumbbell model.

Based on the [`DiskCell`](@ref) model, with a few key differences

  * orientation inheritance can be disabled using the `orientationretention` parameter
  * pairwise cell-cell traction force along axis, scaled with `motility` parameter
  * randomised direction reversal with `basalreversalrate` parameter

Refer to [T. Sunkel, L. Hupe, and P. Bittihn, arXiv:2403.11002 (2024)](https://doi.org/10.48550/arXiv.2403.11002) for a detailed description of the model.

# Extended help

## List of fields

  * `id`, `centerpos`, `params`: InPartS standard fields
  * `nodeseparation`: length of the cell backbone measured between the centres of the circular caps
  * `φ`: orientation of the cell backbone
  * `growthprog`: current growth phase of the cell
  * `grothrate`: rate of change of `growthprog`
  * `attached`: if set to true, evolution of every degree of freedom (except for `growthprog`) is stopped. *Currently unused*.
  * `P`, `N`: node positions
  * `fP`, `fN`: node force accumulators
  * `reversaltimer`: time units until until next orientation reversal
  * `vtrans`, `ωspin`: translational velocity and spin angular velocity
