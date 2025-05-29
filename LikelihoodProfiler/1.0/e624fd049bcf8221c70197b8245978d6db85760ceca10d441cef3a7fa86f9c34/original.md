```
CICOProfiler
```

Confidence Intervals by Constrained Optimization (CICO) method to find the intersections of the likelihood function with the threshold. See [CICOBase docs](https://github.com/insysbio/CICOBase.jl) for more details. Requires `using CICOBase`.

### Fields

  * `optimizer::Symbol`: The optimizer used for the optimization process. Defaults to NLopt `:LN_NELDERMEAD`.
  * `scan_tol::Float64`: The tolerance for the endpoints scan. Defaults to `1e-3`.

### Example

```julia
profiler = CICOProfiler(optimizer = :LN_NELDERMEAD, scan_tol = 1e-3)
```
