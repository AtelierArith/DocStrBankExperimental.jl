```
N,D,E,X = ratfn_minimax(f, interval, n, d, w)
```

Top-level function to find a minimax rational-function approximation.

Arguments:

  * f         The function to be approximated. Maps BigFloat -> BigFloat.
  * interval  A tuple giving the endpoints of the interval           (in either order) on which to approximate f.
  * n, d      The degrees of the numerator and denominator of the desired           approximation.
  * w         Error-weighting function. Takes two BigFloat arguments x,y           and returns a scaling factor for the error at that location.           The returned approximation R should have the minimum possible           maximum value of abs((f(x)-R(x)) * w(x,f(x))). Optional           parameter, defaulting to the always-return-1 function.

Return values: a tuple (N,D,E,X), where

  * N,D       A pair of arrays of BigFloats giving the coefficients           of the returned rational function. N has size n+1; D           has size d+1. Both start with the constant term, i.e.           N[i] is the coefficient of x^(i-1) (because Julia           arrays are 1-based). D[1] will be 1.
  * E         The maximum weighted error (BigFloat).
  * X         An array of pairs of BigFloats giving the locations of n+2           points and the weighted error at each of those points. The           weighted error values will have alternating signs, which           means that the Chebyshev alternation theorem guarantees           that any other function of the same degree must exceed           the error of this one at at least one of those points.
