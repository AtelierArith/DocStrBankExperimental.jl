```
LUSIM()
```

The LU simulation method introduced by Alabert 1987 and Davis 1987.

The full covariance matrix is built to include all locations of the data, and samples from the multivariate Gaussian are drawn via a lower-upper (LU) matrix factorization.

## References

  * Alabert 1987. [The practice of fast conditional simulations through the LU decomposition of the covariance matrix](https://link.springer.com/article/10.1007/BF00897191)
  * Davis 1987. [Production of conditional simulations via the LU triangular decomposition of the covariance matrix](https://link.springer.com/article/10.1007/BF00898189)
  * Oliver 2003. [Gaussian cosimulation: modeling of the cross-covariance](https://link.springer.com/article/10.1023%2FB%3AMATG.0000002984.56637.ef)

### Notes

The method is only adequate for domains with relatively small number of elements (e.g. 100x100 grids) where it is feasible to factorize the full covariance.

For larger domains (e.g. 3D grids), other methods are preferred such as [`SEQSIM`](@ref) and [`FFTSIM`](@ref).
