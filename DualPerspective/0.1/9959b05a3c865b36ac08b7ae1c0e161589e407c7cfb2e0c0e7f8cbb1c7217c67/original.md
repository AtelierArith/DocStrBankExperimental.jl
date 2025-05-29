```
solve!(kl::DPModel, ::SequentialSolve; kwargs...) -> ExecutionStats
```

Solve the KL-regularized least squares problem by finding the optimal scaling parameter `t`  that maximizes the dual objective. The optimal `t` is found by applying root-finding to the derivative of the dual objective with respect to `t`.

# Arguments

  * `kl`: The KL-regularized least squares model to solve
  * `::SequentialSolve`: The sequential solve algorithm type

# Keyword Arguments

  * `t::Real=1.0`: Initial guess for the scaling parameter
  * `rtol::Real=1e-6`: Relative tolerance for the root-finding optimization
  * `atol::Real=1e-6`: Absolute tolerance for the root-finding optimization
  * `xatol::Real=1e-6`: Absolute tolerance for convergence in `t`
  * `xrtol::Real=1e-6`: Relative tolerance for convergence in `t`
  * `δ::Real=1e-2`: Tolerance factor applied to `atol` and `rtol` for the inner optimization
  * `zverbose::Bool=false`: Whether to print verbose output from root-finding
  * `logging::Int=0`: Logging level (0=none, 1=basic, 2=detailed)

# Returns

An `ExecutionStats` struct containing:

  * Solution status
  * Runtime statistics
  * Optimal primal and dual solutions
  * Residuals and optimality measures
