Compute an approximate partial Schur decomposition of a square matrix A

```
partial_schur, _ = jdqr(A, pairs = 5)
```

Accepts the following keyword arguments:

  * `pairs`: number of Schur vectors and values requested
  * `subspace_dimensions`: a range `min:max` that determines the size of the search subspace. In every outer iteration the search subspace is expanded to the `max` size and then  trimmed to the `min` size. When the search subspace is trimmed, the best approximate Schur vectors are kept. A large search subspace speeds up convergence, but is computationally  more expensive. It is advisable to set `min` a bit larger than `pairs`.
  * `max_iter`: maximum number of steps. If the algorithm exceeds `max_iter` steps, it might not have converged for all `pairs` of Schur vectors.
  * `target`: determines which eigenvalues to find. Options: Near(σ) where σ is a complex number in the complex plane near which we want to find eigenvalues; LargestMagnitude(σ),  SmallestMagnitude(σ), LargestRealPart(σ), SmallestRealPart(σ), LargestImaginaryPart(σ), SmallestImaginaryPart(σ), where σ is a complex number / an educated guess.
  * `tolerance`: the accuracy at which Schur vectors are considered converged, based on  the residual norm.
  * `solver`: An iterative correction equation solver used for the expansion of the search subspace.
  * `verbosity=0` silent, `verbosity==1` prints a progress bar, `verbosity==2` prints more detailed debug output.
