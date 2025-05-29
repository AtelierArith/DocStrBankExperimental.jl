```
kernel_eigs(xs::AbstractArray, ϵ::Number, nev::Integer, σ::Number,
            boundary_weights::Vector; kernel::Symbol=:SquaredExponential,
            zero_mean = false, check = 1)
```

Solve the the invariant eigenvalue problem, given by the Rayleigh quotient
> `min_c (‖GKc‖² + ‖Kc‖²_bd + ϵ‖c‖²_k)/‖Kc‖²` 
where

  * `‖GKc‖²` is a norm penalizing invariance (and possible a non-zero mean)
  * `‖Kc‖²_bd` is a norm penalizing boundary violation
  * `‖c‖²_k` is the smoothing kernel norm
  * `‖Kc‖²` is the ℓ² norm of the points

The eigenvalue problem is solved via `Arpack.jl`

Arguments:

  * `xs`: interpolation points of size d × 2N, where xs[:, N+1:2N] = F.(xs[:, 1:N])
  * `ϵ`: Amount of regularization
  * `nev`: Number of eigenvalues to find
  * `σ`: Kernel width
  * `boundary_weights`: Boundary weighting vector, should be positive and O(1) at points `x` where one wants |k(x)| << 1
  * `kernel`: Type of kernel to interpolate (see `KernelLabel`)
  * `zero_mean = false`: Set to true to add a constraint that encourages `k` to have a zero mean. Useful when `xs` are sampled on an invariant set and boundary_weights=0
  * `check = 1`: See `Arpack.eigs`. If 1, return all of the converged eigenvectors and eigenvalues. If 0, throw an error instead.

Output:

  * `λs`: The eigenvalues
  * `vs`: The eigenvectors
  * `k`: The kernel label. Use `set_c!(k, vs[:,n])` to load the `n`th eigenvector into `k`. By default, `k` stores the lowest order eigenvector.
