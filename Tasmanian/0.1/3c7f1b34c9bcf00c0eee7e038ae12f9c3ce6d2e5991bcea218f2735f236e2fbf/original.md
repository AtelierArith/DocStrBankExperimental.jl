```
removePointsByHierarchicalCoefficient!(tsg::TasmanianSG, tolerance, output = -1, scale_correction = [], NumKeep = -1)
```

removes any points in the grid with relative surplus that exceeds the tolerance or keeps the set number of points with largest surplus

tolerance: float (positive)            the relative surplus tolerance, i.e.,            we keep only for points associated with surplus            that exceeds the tolerance            if NumKeep is positive, then tolerance is ignored

output: int (indicates the output to use)         selects which output to consider         accept -1 to indicate all outputs

scale_correction: vector or matrix                   if output = -1 and getNumOutputs() > 1,                   then using matrix with shape                   getNumOutputs() X getNumLoaded() with                   one weight per hierarchical coefficient                   if output > -1, then using a vector with                   one weight per point

NumKeep: int (positive or equal to -1)          indicates the number of points to keep          if set to -1 then tolerance is used as a cutoff          if positive then the given number of points will be kept
