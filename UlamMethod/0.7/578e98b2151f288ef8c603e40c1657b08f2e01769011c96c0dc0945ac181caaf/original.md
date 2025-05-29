```
abstract type ReinjectionAlgorithm
```

The abstract type for the algorithm controlling how trajectories pointing from nirvana to the interior are redistributed.

Each subtype `reinj_algo` should implement the following:

  * a function `reinject!(binner, Pij, reinj_algo)` that modifies the transition matrix `Pij`in place given

the binning algorithm `binner`. This function is applied after the largest strongly connected component of the original `Pij` is taken, but before the matrix is row-stochasticized. 
