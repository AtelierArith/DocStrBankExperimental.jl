```
Tolerance
```

A struct specifying the different tolerances used to assess the convergence of the algorithms. The following are the fields of `Tolerance`:

  * `x`: the tolerance for `Δx` in [`ConvergenceState`](@ref). `x_converged` will be true if `Δx` is less than the `x` tolerance in `Tolerance`. This is used to assess convergence when the [`GenericCriteria`](@ref) is used as the convergence criteria.
  * `fabs`: the tolerance for `Δf` in [`ConvergenceState`](@ref). `f_converged` will be true if `Δf` is less than the `fabs` tolerance in `Tolerance`. This is used to assess convergence when the [`GenericCriteria`](@ref) is used as the convergence criteria.
  * `frel`: the tolerance for `relΔf` in [`ConvergenceState`](@ref). `f_converged` will be true if `relΔf` is less than the `frel` tolerance in `Tolerance`. This is used to assess convergence when the [`GenericCriteria`](@ref) is used as the convergence criteria.
  * `kkt`: the KKT tolerance. `kkt_converged` in [`ConvergenceState`](@ref) will be true if the `kkt_residual` is less than the KKT tolerance. And `ipopt_converged` in [`ConvergenceState`](@ref) will be true if `ipopt_residual` is less than the KKT tolerance. This is used to assess convergence when the [`KKTCriteria`](@ref), the [`ScaledKKTCriteria`](@ref) or [`IpoptCriteria`](@ref) criteria is used as the convergence criteria.
  * `infeas`: the maximum infeasibility tolerance. `infeas_converged` in [`ConvergenceState`](@ref) will be true if the maximum infeasibility is less than the infeasibility tolerance. This is used to assess convergence regardless of the convergence criteria used.

For more on convergence criteria, see [`GenericCriteria`](@ref), [`KKTCriteria`](@ref), [`ScaledKKTCriteria`](@ref) and [`IpoptCriteria`](@ref).
