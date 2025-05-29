```julia
struct GeomSum{F} <: PEPSKit.GradMode{F}
```

Gradient mode for CTMRG using explicit evaluation of the geometric sum.

## Fields

  * `tol::Real`
  * `maxiter::Int64`
  * `verbosity::Int64`

## Constructors

```
GeomSum(; kwargs...)
```

Construct the `GeomSum` algorithm struct based on the following keyword arguments:

  * `tol::Real=1.0e-6` : Convergence tolerance for the difference of norms of two consecutive summands in the geometric sum.
  * `maxiter::Int=30` : Maximal number of gradient iterations.
  * `verbosity::Int=-1` : Output information verbosity that can be one of the following:

    0. Suppress output information
    1. Print convergence warnings
    2. Information at each gradient iteration
  * `iterscheme::Symbol=:fixed` : Style of CTMRG iteration which is being differentiated, which can be:

      * `:fixed` : the differentiated CTMRG iteration uses a pre-computed SVD with a fixed set of gauges
      * `:diffgauge` : the differentiated iteration consists of a CTMRG iteration and a subsequent gauge-fixing step such that the gauge-fixing procedure is differentiated as well
