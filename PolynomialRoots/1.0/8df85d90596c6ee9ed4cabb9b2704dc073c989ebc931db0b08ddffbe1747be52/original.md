```
roots5(polynomial[, roots]; epsilon=1e-20) -> roots
```

Find all the roots of `polynomial`, of degree 5 only.

Mandatory argument:

  * `polynomial`: vector of 6 coefficients (type `Number`) of the polynomial of which to find the roots, from the lowest coefficient to the highest one

Optional argument:

  * `roots`: vector of initial guess roots (of length 5).  If you have a very rough idea where some of the roots can be, this vector is used as starting value for Laguerre's method and the provided roots will be only polished

Optional keyword:

  * `epsilon` (`AbstractFloat`): this is used to determine the stopping criterion described in Skowron & Gould paper.  If not set, it defaults to machine precision of `polynomial` (and `roots`) argument(s).  This is *not* the precision with which the roots will be calculated

Function `roots` can be used to find roots of polynomials of any degree.
