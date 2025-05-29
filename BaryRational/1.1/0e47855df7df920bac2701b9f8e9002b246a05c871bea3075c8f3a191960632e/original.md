```
aaa(Z, F; tol=1e-13, mmax=150, verbose=false, clean=true, do_sort=false) -> r::AAAapprox
```

Computes the rational approximation of data `F` on set `Z` using the AAA algorithm.

# Arguments

  * `Z`: Vector of sample points.
  * `F`: Vector of values at the points in `Z`.
  * `tol`: Relative tolerance.
  * `mmax`: Degree of numerator and denominator is at most `(mmax-1, mmax-1)`.
  * `verbose`: If `true`, prints detailed information during computation.
  * `clean`: If `true`, detects and removes Froissart doublets.
  * `do_sort`: If `true` sorts the values of `Z` (and correspondingly `F`) in ascending order.

# Returns

  * `r::AAAapprox`: A  struct representing the approximant that called as a function. The  struct has fields, `z, f, w` = vectors of support points, function values, weights and  `errvec` = vector of errors at each step.

Note 1. Changes from the MATLAB version include: Switched order of `Z` and `F` in the function signature. Added `verbose` and `clean` boolean flags. Poles, residues, and zeros (`pol`, `res`, `zer`) are calculated on demand by calling `prz(z::AAAapprox)`.

Note 2. The code (more or less) works with `BigFloat`. Since `prz` has not been made generic, when using `BigFloat`, set `clean=false`. Specify `tol` as a tiny `BigFloat` value explicitly, as default tolerances may not be sufficient.

# Example

```julia
    using BaryRational
    xrat = [-1//1:1//100:1//1;];
    xbig = BigFloat.(xrat);
    fbig = sin.(xbig);
    sf = aaa(xbig, fbig, verbose=true, clean=false, tol=BigFloat(1/10^40));

    julia @v1.10> sin(BigFloat(-1//3))
    -0.3271946967961522441733440852676206060643014068937597915900562770705763744817618

    julia @v1.10> sf(BigFloat(-1//3))
    -0.3271946967961522441733440852676206060643014068937597915900562770705763744817662
```
