```
bat_integrated_autocorr_len(
    v::AbstractVectorOfSimilarVectors{<:Real};
    c::Integer = 5, tol::Integer = 50, strict = true
)
```

Estimate the integrated autocorrelation length of variate series `v`.

  * `c`: Step size for window search.
  * `tol`: Minimum number of autocorrelation times needed to trust the estimate.
  * `strict`: Throw exception if result is not trustworthy

This estimate uses the iterative procedure described on page 16 of [Sokal's notes](http://www.stat.unc.edu/faculty/cji/Sokal.pdf) to determine a reasonable window size.

Ported to Julia from the emcee Python package, under MIT License. Original authors Dan Foreman-Mackey et al.
