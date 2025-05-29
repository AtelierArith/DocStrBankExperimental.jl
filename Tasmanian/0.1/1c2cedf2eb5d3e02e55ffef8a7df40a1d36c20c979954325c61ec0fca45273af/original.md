```
evaluateSparseHierarchicalFunctions(tsg::TasmanianSG, x)
```

evaluates the hierarchical functions at a set of points in the domain. The distinction between this function and evaluateHierarchicalFunctions() lies in the type of the returned result, namely a sparse vs a dense matrix.

The motivation for this function is that Local Polynomial and Wavelet grids usually result in sparse matrices

x: a matrix with dimensions getNumDimensions() by NumX       the entries indicate the points for evaluating

output: returns a TasmanianSimpleSparseMatrix class         which is a simple class with three fields:         aPntr, aIndx, and aVals which are numpy.ndarray of types         int32, int32, and float64         NumRows and NumCols are meta fields and have values         NumRows = x.shape[0]         NumCols = getNumPoints()         The sparse matrix is compressed along the x.shape[0]         dimension, i.e., using column compressed format
