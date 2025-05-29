```
init(::ParaReal.Problem,
     ::ParaReal.Algorithm;
     kwargs...)
```

Initialize a pipeline to eventually run on the worker ids specified by `workers`. Do not start the tasks executing the pipeline stages.

Returns a [`Pipeline`](@ref).

# Keyword Arguments

  * `schedule::ParaReal.Schedule = ProcessesSchedule()`: specify how to distributed/schedule the tasks executing the stages
  * `maxiters = 10`: maximum number of Newton refinements, `k <= K = maxiters`
  * `nconverged = 2`: number of consequtive refinements without significant change; used to reason about convergence (more details below); set to `typemax(Int)` to disable convergence checks altogether
  * `rtol::Float64 = size(iv, 1) * eps()`: relative error, where `iv = initial_value(prob.p)`; used to reason about convergence (more details below)
  * `atol::Float64 = 0.0`: absolute error; used to reason about convergence (more details below)
  * `logger = nothing`: where to log messages on the pipeline stages. If `nothing`, use `current_logger()` on the respective workers. Errors will be rethrown outside `with_logger(logger) do ... end`, i.e. handled by the global logger.
  * `warmupc::Bool = true`: controls JIT-warmup of `csolve`, cf. [`Algorithm`](@ref)
  * `warmupf::Bool = false`: controls JIT-warmup of `fsolve`, cf. [`Algorithm`](@ref)

# Convergence

A refinement `Uᵏ` showed no significant change if

```
dist(Uᵏ, Uᵏ⁻¹) <= max(atol, max(norm(Uᵏ), norm(Uᵏ⁻¹)) * rtol)
```

using [`dist`](@ref) and `LinearAlgebra.norm`. As computing `norm(Uᵏ)` might be expensive, its value is cached between iterations. Other than that, this works essentially like `isapprox`.

A stage `n` is considered to have converged, if

1. `>= nconverged` successive refinements showed no significant change, and
2. the previous stage `n-1` needed to compute at most 1 refinement more, i.e. `k(n) >= k(n-1) - 1`.

Due to the second criterion, `> nconverged` refinements without significant change might have been computed.

Disable convergence checks by setting `nconverged` to `typemax(Int)`. Then, neither `dist` nor `norm` will be computed; they don't even require special methods for custom solution types.
