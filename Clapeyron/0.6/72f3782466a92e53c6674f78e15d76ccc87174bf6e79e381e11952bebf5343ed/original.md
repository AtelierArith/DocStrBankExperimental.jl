```
tpd(model,p,T,z;break_first = false,lle = false,tol_trivial = 1e-5, di = nothing)
```

Calculates the Tangent plane distance function (`tpd`). It returns:

  * a vector with trial phase compositions where `tpd < 0`
  * a vector with the `tpd` values
  * a vector with symbols indicating the phase of the input composition
  * a vector with symbols indicating the phase of the trial composition

It iterates over each two-phase combination, starting from pure trial compositions, it does succesive substitution, then Gibbs optimization.

If the vectors are empty, then the procedure couldn't find a negative `tpd`. That is an indication that the phase is (almost) surely stable.
