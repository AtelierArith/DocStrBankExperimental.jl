```
rsvd_fnkz(A, k)
```

Compute the randomized SVD by iterative refinement from randomly selected columns/rows [^Friedland2006].

# Arguments

  * `A`: matrix whose SVD is desired;
  * `k::Int`: desired rank of approximation (`k ≤ min(m, n)`).

## Keywords

  * `l::Int = k`: number of columns/rows to sample at each iteration (`1 ≤ l ≤ k`);
  * `N::Int = minimum(size(A))`: maximum number of iterations;
  * `ϵ::Real = prod(size(A))*eps()`: relative threshold for convergence, as measured by growth of the spectral norm;
  * `method::Symbol = :eig`: problem to solve.

    1. `:eig`: eigenproblem.
    2. `:svd`: singular problem.
  * `verbose::Bool = false`: print convergence information at each iteration.

# Return value

SVD object of `rank ≤ k`.

[^Friedland2006]: Friedland, Shmuel, et al. "Fast Monte-Carlo low rank approximations for  matrices." System of Systems Engineering, 2006 IEEE/SMC International  Conference on. IEEE, 2006.
