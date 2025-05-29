```
rd(X, Y; typ = :cor)
rd(X, Y, weights::Weight; typ = :cor)
```

Compute redundancy coefficients (Rd).

  * `X` : Matrix (n, p).
  * `Y` : Matrix (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `typ` : Possibles values are: `:cor` (correlation),    `:cov` (uncorrected covariance).

Returns the redundancy coefficient between `X` and each column of `Y`, i.e. for each k = 1,...,q: 

  * Mean {cor(xj, yk)^2 ;  j = 1, ..., p }

Depending argument `typ`, the correlation can be replaced by the (not corrected)  covariance.

See Tenenhaus 1998 section 2.2.1 p.10-11.

## References

Tenenhaus, M., 1998. La régression PLS: théorie et pratique.  Editions Technip, Paris.

## Examples

```julia
using Jchemo
X = rand(5, 10)
Y = rand(5, 3)
rd(X, Y)
```
