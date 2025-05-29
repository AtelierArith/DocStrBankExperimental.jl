```
KMedoids(k; tol=1e-4, maxiter=10, weights=nothing, rng=Random.default_rng())
```

Assign labels to rows of table using the `k`-medoids algorithm.

The iterative algorithm is interrupted if the relative change on the average distance to medoids is smaller than a tolerance `tol` or if the number of iterations exceeds the maximum number of iterations `maxiter`.

Optionally, specify a dictionary of `weights` for each column to affect the underlying table distance from TableDistances.jl, and a random number generator `rng` to obtain reproducible results.

## Examples

```julia
KMedoids(3)
KMedoids(4, maxiter=20)
KMedoids(5, weights=Dict(:col1 => 1.0, :col2 => 2.0))
```

## References

  * Kaufman, L. & Rousseeuw, P. J. 1990. [Partitioning Around Medoids (Program PAM)](https://onlinelibrary.wiley.com/doi/10.1002/9780470316801.ch2)
  * Kaufman, L. & Rousseeuw, P. J. 1991. [Finding Groups in Data: An Introduction to Cluster Analysis](https://www.jstor.org/stable/2532178)
