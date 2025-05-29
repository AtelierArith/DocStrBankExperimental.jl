```
estimateAnisotropicCoefficients(tsg::TasmanianSG, type, output)
```

returns the estimate of the anisotropic coefficients from the current set of loaded points see the manual

type: string identifying the estimate to use (see the Manual)        recommended: 'iptotal'   'ipcurved'

output: int (indicates the output to use)      selects which output to use for refinement      sequence grids accept -1 to indicate all outputs

returns vector of length getNumDimensions() or 2*getNumDimensions()         the first set of getNumDimensions() entries correspond to the xi coefficients          the second set of getNumDimensions() entries correspond to the eta coefficients
