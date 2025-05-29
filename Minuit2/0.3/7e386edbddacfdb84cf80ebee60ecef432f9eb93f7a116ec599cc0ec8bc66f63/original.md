```
mnprofile(m::Minuit, var; size=30, bound=2, grid=nothing, subtract_min=false, 
               ncall=0, iterate=5, use_simplex=true)
```

Get Minos profile over a specified interval.

Scans over one parameter and minimises the function with respect to all other parameters for each scan point.

## Arguments

  * `var` : Parameter to scan over.
  * `size=30` : Number of scanning points. Ignored if grid is set.
  * `bound=2` : If bound is a tuple, (left, right) scanning bound, or the number of sigmas to scan symmetrically around the minimum. Ignored if grid is set.
  * `grid` : Parameter values on which to compute the profile. If `grid` is set, `size` and  `bound` are ignored.
  * `subtract_min=false` : If true, subtract offset so that smallest value is zero.
  * `ncall=0` : Approximate maximum number of calls before minimization will be aborted.  If set to 0, use the adaptive heuristic from the Minuit2 library.   Note: The limit may be slightly violated, because the condition is checked only after   a full iteration of the algorithm, which usually performs several function calls.       iterate : int, optional           Automatically call Migrad up to N times if convergence was not reached           (Default: 5). This simple heuristic makes Migrad converge more often even if           the numerical precision of the cost function is low. Setting this to 1           disables the feature.       use_simplex: bool, optional           If we have to iterate, set this to True to call the Simplex algorithm before           each call to Migrad (Default: True). This may improve convergence in           pathological cases (which we are in when we have to iterate).

## Returns

  * Tuple(`x`, `y`, `ok`) : Tuple of 1D arrays with the parameter values, function values and booleans whether the fit succeeded or not.
