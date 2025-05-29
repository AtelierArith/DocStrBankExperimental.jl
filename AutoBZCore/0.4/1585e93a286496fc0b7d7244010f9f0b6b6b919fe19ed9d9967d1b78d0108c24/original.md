```
AutoBZProblem([rep], f, bz, [p]; kwargs...)
```

Construct a BZ integration problem.

## Arguments

  * `rep::AbstractSymRep`: The symmetry representation of `f` (default: `UnknownRep()`)
  * `f::AbstractIntegralFunction`: The integrand
  * `bz::SymmetricBZ`: The Brillouin zone to integrate over
  * `p`: parameters for the integrand (default: `NullParameters()`)

## Keywords

Additional keywords are passed directly to the solver
