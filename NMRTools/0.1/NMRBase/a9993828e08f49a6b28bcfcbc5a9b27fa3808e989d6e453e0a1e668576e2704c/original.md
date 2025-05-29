```
setkinetictimes(A::NMRData, [dimnumber], tvals, units="")
```

Return a new NMRData with a kinetic time axis containing the passed values (and optionally, units). If a dimension number is specified, that dimension will be replaced with a `TkinDim`. If not, the function will search for a unique non-frequency dimension, and replace that. If there are multiple non-frequency dimensions, the dimension number must be specified explicitly, and the function will throw an error.
