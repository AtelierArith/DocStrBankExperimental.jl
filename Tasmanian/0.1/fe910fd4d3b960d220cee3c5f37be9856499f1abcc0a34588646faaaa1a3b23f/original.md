```
setHierarchicalCoefficients!(tsg::TasmanianSG, coefficients)
```

Local polynomial, Wavelet, and Sequence grids construct  approximation using hierarchical coefficients based on the  loaded values. This function does the opposite, the hierarchical  coefficients are loaded directly and the values are computed  based on the coefficients. The coefficients can be computed,  e.g., by solving least-squares or compressed sensing problem             min || A c - f ||  where A is a matrix returned by evaluateHierarchicalFunctions()  or evaluateSparseHierarchicalFunctions() for a set of points  x; f are the values of the target function at the x  points; and c is the vector with corresponding hierarchical  coefficients.

If there is a pending refinement, i.e., getNumLoaded() != 0 and  getNumNeeded() != 0, then the refinement is discarded (since it  was computed based on the old and now obsolete values)

coefficients: a matrix with dimensions getNumOutputs() by getNumPoints()                each column corresponds to the values of the                coefficients at the corresponding point.                The order and leading dimension must match the                points obtained form getPoints(), the same                order as the second dimension of                evaluateHierarchicalFunctions().                This matrix must be of type Matrix{ComplexF64} when                using a Fourier grid.
