```
setAnisotropicRefinement!(tsg::TasmanianSG, type, min_growth, output, level_limits = Vector{Int32}(undef, 0))
```

estimates anisotropic coefficients from the current set of loaded points and updates the grid with the best points according to the estimate

type: string identifying the estimate to use (see the Manual)       recommended: 'iptotal'   'ipcurved'

min_growth: int (positive)             minimum number of new points to include in the new grid

output: int (indicates the output to use) selects which output to use for refinement         sequence grids, using -1 indicates to use all outputs

level_limits: (if not empty) will be used to overwrite the currently set limits. The limits must be either empty               or have size getNumDimensions(); if empty, the current set of limits will be used.
