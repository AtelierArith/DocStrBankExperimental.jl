```
abstract type CombinatorialSolution
```

The solution returned by a solver when calling the `solve` function.  This type should be specified for each combinatorial instance to have  a unified solution type.

Two fields must be implemented: `instance` must be the instance that has been solved, and `variables` must indicate the actual solution. `variables` can only contain the discrete items that are chosen as part of the solution (i.e., the  elements of this object can be used as indices for the rewards of a  `CombinatorialInstance`). Solution objects can define more properties  if needed.
