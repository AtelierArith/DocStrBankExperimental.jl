```
kernel_bvp(xs::AbstractArray, ϵ::Number, σ::Number,
           boundary_weights::AbstractVector,
           boundary_values::AbstractVector;
           kernel::Symbol=:SquaredExponential, residuals::Bool=true)
```

Solve the the invariant boundary value least-squares problem
> `min_c ‖GKc‖² + ‖Kc - h_{bd}‖²_bd + ϵ‖c‖²_k = R_inv + R_bd + R_eps`
where

  * `‖GKc‖²` is a norm penalizing invariance (and possible a non-zero mean)
  * `‖Kc - h_{bd}‖²_bd` is a norm penalizing the function from violating the boundary condition
  * `‖c‖²_k` is the smoothing kernel norm

Arguments:

  * `xs`: interpolation points of size d × 2N, where xs[:, N+1:2N] = F.(xs[:, 1:N])
  * `ϵ`: Amount of regularization
  * `σ`: Kernel width
  * `boundary_weights`: Length `2N` boundary weighting vector, should be positive and O(1) at points `x` where one wants |k(x)| << 1
  * `boundary_values`: Length `2N` boundary value vector, indicating the value the function should take at each point
  * `kernel=:SquaredExponential`: Type of kernel to interpolate (see `KernelLabel`)
  * `residuals=true`: True if you want the problem to return residuals.

Output:

  * `k`: The kernel function

(if `residuals=true`)

  * `R`: The total residual
  * `R_bd`: The boundary condition residual
  * `R_inv`: The invariance residual
  * `R_eps`: The smoothness residual
