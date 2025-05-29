```
GSN_radial(s::Int, l::Int, m::Int, a, omega, boundary_condition, rsin, rsout; horizon_expansion_order::Int=_DEFAULT_horizon_expansion_order, infinity_expansion_order::Int=_DEFAULT_infinity_expansion_order, method="auto", data_type=Solutions._DEFAULTDATATYPE,  ODE_algorithm=Solutions._DEFAULTSOLVER, tolerance=Solutions._DEFAULTTOLERANCE, rsmp=nothing)
```

Compute the GSN function for a given mode (specified by `s` the spin weight, `l` the harmonic index, `m` the azimuthal index, `a` the Kerr spin parameter, and `omega` the frequency [which *can be complex*])  and boundary condition specified by `boundary_condition`, which can be either

```
- `IN` for purely-ingoing at the horizon,
- `UP` for purely-outgoing at infinity,
- `OUT` for purely-outgoing at the horizon,
- `DOWN` for purely-ingoing at infinity.
```

Note that the `OUT` and `DOWN` solutions are constructed by linearly combining the `IN` and `UP` solutions, respectively.

The GSN function is numerically solved, for real values of `omega`, in the interval of *tortoise coordinates* $r_{*} \in$ `[rsin, rsout]` using the ODE solver (from `DifferentialEquations.jl`) specified by `ODE_algorithm` (default: `Vern9()`)  with tolerance specified by `tolerance` (default: `1e-12`). The ODE to be solved is determined by the keyword `method` (default: `auto`), which can be either `linear` (solving the GSN equation in a linear form) or `Riccati` (solving the GSN equation in a nonlinear form). By default the data type used is `ComplexF64` (i.e. double-precision floating-point number) but it can be changed by specifying `data_type` (e.g. `Complex{BigFloat}` for complex arbitrary precision number).

With complex values of `omega`, the GSN function is solved along a rotated path on the complex plane of $r_*$,  where the path consists of two broken line segments parametrized by a real variable/a new coordinate $\rho$. The angle with which the path is rotated is determined by the frequency $\omega$, the Kerr spin parameter $a$ and the azimuthal index $m$,  such that the GSN function still behaves like a plane wave near the horizon and spatial infinity.  At $\rho = 0$, the path intersects with the real axis at $r_{*} = r_{*}^{\rm{mp}}$ (`rsmp`, default to be nothing, which means it will be determined automatically). Both the numerical and semi-analytical GSN solutions are evaluated as functions of $\rho$ instead of the now-complex $r_{*}$.

While the numerical GSN solution is only accurate in the range `[rsin, rsout]`,  the full GSN solution is constructed by smoothly attaching the asymptotic solutions near horizon (up to `horizon_expansion_order`-th order)  and infinity (up to `infinity_expansion_order`-th order). Therefore, the now-semi-analytical GSN solution is *accurate everywhere*.

Note, however, when `omega = 0`, the exact GSN function expressed using Gauss hypergeometric functions will be returned (i.e., instead of being solved numerically).  In this case, only `s`, `l`, `m`, `a`, `omega`, `boundary_condition` will be parsed.

Return a `GSNRadialFunction` object which contains all the information about the GSN solution.
