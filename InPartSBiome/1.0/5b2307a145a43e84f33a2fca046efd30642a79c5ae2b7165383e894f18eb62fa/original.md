```
SpheroidDiskCellParams
```

Parameters for [`SpheroidDiskCell`](@ref)s.

Refer to [T. Sunkel, L. Hupe, and P. Bittihn, arXiv:2403.11002 (2024)](https://doi.org/10.48550/arXiv.2403.11002) for a detailed description of the model.

# Extended help

## List of fields

  * `motility`: scales the cell-cell traction forces
  * `radius`: radius.
  * `youngsmodulus`: cell hardness
  * `inthardnessfactor`: internal hardness relative to external hardness. Default value is `1.0`.
  * `viscosity`: uniformly scales cell mobilities
  * `intmobilityfactor`: sets ratio between parallel translational and internal mobilities.
  * `growthrateretention`: weight of inherited component of child growth rates
  * `growthratedistribution`: distribution of random component of child growth rate
  * `orientationretention`: Sets the influence of parent orientation on child orientation, currently only accepts `Inf` (perfect inheritance) or `0` (uncorrelated random orientations)
  * `basalreversalrate`: Sets the rate of orientation reversal

```

```
