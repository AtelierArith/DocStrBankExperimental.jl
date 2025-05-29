```
IntegrationProfiler{opType, optsType, DEAlg, DEOpts}
```

A profiler method that uses integration of differential equations system to profile the likelihood function.

### Fields

  * `reoptimize::Bool`: Indicates whether to re-optimization after each step of the `integrator`. Defaults to `false`.
  * `optimizer::opType`: The optimizer used for the optimization process. Defaults to `nothing`.
  * `optimizer_opts::optsType`: Options for the optimizer. Defaults to `NamedTuple()`.
  * `integrator::DEAlg`: The differential equation algorithm used for integration.
  * `integrator_opts::DEOpts`: Options for the differential equation solver. Defaults to `NamedTuple()`.
  * `matrix_type::Symbol`: The type of matrix to be used for the Hessian approximation. Possible options are: `:hessian`, `:identity`. Defaults to `:hessian`.
  * `gamma::Float64`: Correction factor used in integration if full hessian is not computed (e.g. `matrix_type = :identity`). Defaults to `1.0`.

### Example

```julia
using OrdinaryDiffEq
profiler = IntegrationProfiler(integrator = Tsit5(), integrator_opts = (dtmax=0.3,), matrix_type = :hessian)
```
