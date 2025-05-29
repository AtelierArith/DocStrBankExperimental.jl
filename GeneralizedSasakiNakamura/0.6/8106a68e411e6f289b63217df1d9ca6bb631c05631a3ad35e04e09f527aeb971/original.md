```
Teukolsky_radial(s::Int, l::Int, m::Int, a, omega, boundary_condition, rsin, rsout; horizon_expansion_order::Int=_DEFAULT_horizon_expansion_order, infinity_expansion_order::Int=_DEFAULT_infinity_expansion_order, method="auto", data_type=Solutions._DEFAULTDATATYPE,  ODE_algorithm=Solutions._DEFAULTSOLVER, tolerance=Solutions._DEFAULTTOLERANCE, rsmp=nothing)
```

Compute the Teukolsky function for a given mode (specified by `s` the spin weight, `l` the harmonic index, `m` the azimuthal index, `a` the Kerr spin parameter, and `omega` the frequency [which *can be complex*])  and boundary condition specified by `boundary_condition`, which can be either

```
- `IN` for purely-ingoing at the horizon,
- `UP` for purely-outgoing at infinity,
- `OUT` for purely-outgoing at the horizon,
- `DOWN` for purely-ingoing at infinity.
```

Note that the `OUT` and `DOWN` solutions are constructed by linearly combining the `IN` and `UP` solutions, respectively.

The full GSN solution is converted to the corresponding Teukolsky solution $(R(r), dR/dr)$ and  the incidence, reflection and transmission amplitude are converted from the GSN formalism to the Teukolsky formalism  with the normalization convention that the transmission amplitude is normalized to 1 (i.e. `normalization_convention=UNIT_TEUKOLSKY_TRANS`).

Note, however, when `omega = 0`, the exact Teukolsky function expressed using Gauss hypergeometric functions will be returned (i.e., instead of using the GSN formalism).  In this case, only `s`, `l`, `m`, `a`, `omega`, `boundary_condition` will be parsed.

With complex values of `omega`, the Teukolsky function is evaluated as a function of $r$, where the value at the corresponding location $\rho = r_{*}(r) \in \mathbb{R}$ along the rotated integration path on the complex plane is returned.
