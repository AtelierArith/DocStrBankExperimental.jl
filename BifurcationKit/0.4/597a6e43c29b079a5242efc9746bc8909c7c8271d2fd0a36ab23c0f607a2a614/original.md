```julia
predictor(bp, ds; verbose, ampfactor)

```

This function provides prediction for the zeros of the Pitchfork bifurcation point.

# Arguments

  * `bp::Pitchfork` the bifurcation point
  * `ds` at with distance relative to the bifurcation point do you want the prediction. Based on the criticality of the Pitchfork, its sign is enforced no matter what you pass. Basically the parameter is `bp.p + abs(ds) * dsfactor` where `dsfactor = ±1` depending on the criticality.

# Optional arguments

  * `verbose` display information
  * `ampfactor = 1` factor multiplying prediction

# Returned values

  * `x0` trivial solution (which bifurcates)
  * `x1` non trivial guess
  * `p` new parameter value
  * `dsfactor` factor which has been multiplied to `abs(ds)` in order to select the correct side of the bifurcation point where the bifurcated branch exists.
  * `amp` non trivial zero of the normal form
