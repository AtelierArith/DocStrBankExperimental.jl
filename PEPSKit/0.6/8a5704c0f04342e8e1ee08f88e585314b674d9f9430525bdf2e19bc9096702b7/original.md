```julia
struct ManualIter{F} <: PEPSKit.GradMode{F}
```

Gradient mode for CTMRG using manual iteration to solve the linear problem.

## Fields

  * `tol::Real`
  * `maxiter::Int64`
  * `verbosity::Int64`

## Constructors

```
ManualIter(; kwargs...)
```

Construct the `ManualIter` algorithm struct based on the following keyword arguments:

  * `tol::Real=1.0e-6` : Convergence tolerance for the norm difference of two consecutive `dx` contributions.
  * `maxiter::Int=30` : Maximal number of gradient iterations.
  * `verbosity::Int=-1` : Output information verbosity that can be one of the following:

    0. Suppress output information
    1. Print convergence warnings
    2. Information at each gradient iteration
  * `iterscheme::Symbol=:fixed` : Style of CTMRG iteration which is being differentiated, which can be:

      * `:fixed` : the differentiated CTMRG iteration uses a pre-computed SVD with a fixed set of gauges
      * `:diffgauge` : the differentiated iteration consists of a CTMRG iteration and a subsequent gauge-fixing step such that the gauge-fixing procedure is differentiated as well
