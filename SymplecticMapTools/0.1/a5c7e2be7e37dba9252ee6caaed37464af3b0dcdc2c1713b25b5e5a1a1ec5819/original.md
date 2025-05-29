```
kernel_birkhoff(xs::AbstractArray, fs::AbstractVector, ϵ::Number, μ::Number;
                σ::Number=0., kernel::Symbol=:SquaredExponential,
                boundary_points::AbstractVector = [])
```

This function is mostly deprecated. The solutions to the infinitely discretized limit of this problem (the Birkhoff average) don't live in the native space. So, the results can be odd, hard to interpret, and wiggly. Use at your own risk.

Find the "Birkhoff average" of a function using the kernel approach. Solves the least-squares problem
> `min_c μ⁻¹(‖GKc‖² + ‖Kc‖²_bd) + ϵ‖c‖²_k + ‖Kc - f‖²`
where

  * `‖GKc‖²` is a norm penalizing invariance
  * `‖c‖²_k` is the smoothing kernel norm
  * `‖Kc - f‖²` is a least-squares fit norm
  * `‖Kc‖²_bd` is a norm penalizing boundary violation

Arguments:

  * `xs`: interpolation points of size d × 2N, where xs[:, N+1:2N] = F.(xs[:, 1:N])
  * `fs`: function values at points of size N
  * `ϵ`: Amount of regularization (can be set to zero)
  * `μ`: Weighting of invariance penalization to fit (should be small, e.g. 1e-6)
  * `σ`: Scale of the problem
  * `kernel`: Type of kernel to interpolate (see `KernelLabel`)
  * `boundary_points`: A list of indices of points on the boundary

Output:

  * `k`: A KernelLabel object
