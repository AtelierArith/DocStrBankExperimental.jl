```julia
predictor(bp, ds; verbose, ampfactor)

```

This function provides prediction for the zeros of the Transcritical bifurcation point.

# Arguments

  * `bp::Transcritical` the bifurcation point
  * `ds` distance to the bifurcation point for the prediction. Can be negative. Basically the parameter is `p = bp.p + ds`

# Optional arguments

  * `verbose` display information
  * `ampfactor = 1` factor multiplying prediction

# Returned values

  * `x0` trivial solution (which bifurcates)
  * `x1` non trivial guess, corrected with Lyapunov-Schmidt expansion
  * `p` new parameter value
  * `amp` non trivial zero of the normal form (not corrected)
  * `xm1` non trivial guess for the parameter `pm1`
  * `pm1` parameter value `bp.p - ds`
