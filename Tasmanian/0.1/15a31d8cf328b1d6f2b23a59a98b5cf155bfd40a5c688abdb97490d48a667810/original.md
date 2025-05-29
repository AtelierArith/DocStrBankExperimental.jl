```
getInterpolationWeightsBatch(tsg, llfX):
```

returns the interpolation weights associated with the points in getPoints()

finds multiple weights with a single library call uses OpenMP if enabled in libtasmaniansparsegrids.so

x: a matrix with first dimension getNumDimensions()    each column in the array is a single requested point

output: a matrix         with dimensions getNumPoints() X size(llfX, 2)           each row corresponds to the weight for one row of llfX
