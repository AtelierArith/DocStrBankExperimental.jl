```julia
predictor(hp, ds; verbose, ampfactor)

```

This function provides prediction for the periodic orbits branching off the Hopf bifurcation point. If the hopf normal form does not contain the `a,b` coefficients, then a guess if formed with the eigenvector and `ampfactor`. In case it does, a second order predictor is computed.

# Arguments

  * `bp::Hopf` bifurcation point
  * `ds` at with distance relative to the bifurcation point do you want the prediction. Can be negative. Basically the new parameter is `p = bp.p + ds`.

# Optional arguments

  * `verbose` display information
  * `ampfactor = 1` factor multiplied to the amplitude of the periodic orbit.

# Returned values

  * `t -> orbit(t)` 2π periodic function guess for the bifurcated orbit.
  * `amp` amplitude of the guess of the bifurcated periodic orbits.
  * `ω` frequency of the periodic orbit (corrected with normal form coefficients)
  * `period` of the periodic orbit (corrected with normal form coefficients)
  * `p` new parameter value
  * `dsfactor` factor which has been multiplied to `abs(ds)` in order to select the correct side of the bifurcation point where the bifurcated branch exists.
