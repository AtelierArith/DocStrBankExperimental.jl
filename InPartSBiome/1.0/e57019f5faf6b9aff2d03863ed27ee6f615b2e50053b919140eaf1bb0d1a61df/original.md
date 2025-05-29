```
RodCellParams
```

Parameters for [`RodCell`](@ref)s.

Refer to [J. Isensee et al., J. R. Soc. Interface. 19, 20220512 (2022)](https://doi.org/10.1098/rsif.2022.0512) for a description of the model.

# Extended help

## List of fields

  * `maxlength`: nodeseparation of a mature cell (growthprog → 1)
  * `radius`: radius.
  * `youngsmodulus`: cell hardness
  * `inthardnessfactor`: internal hardness relative to external hardness. Default value is `1.0`.
  * `viscosity`: uniformly scales cell mobilities
  * `intmobilityfactor`: sets ratio between parallel translational and internal mobilities.
  * `growthrateretention`: weight of inherited component of child growth rates
  * `growthratedistribution`: distribution of random component of child growth rate
