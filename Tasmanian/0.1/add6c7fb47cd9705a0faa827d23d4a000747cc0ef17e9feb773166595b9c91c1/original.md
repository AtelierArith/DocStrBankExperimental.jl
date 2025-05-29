```
getHierarchicalCoefficients(tsg::TasmanianSG)
```

For global grids, this just returns the values loaded using the call to loadNeededPoints(). In all other cases, this returns the list of hierarchical coefficients, i.e., surpluses.

returns a matrix getNumOutputs() by getNumPoints()
