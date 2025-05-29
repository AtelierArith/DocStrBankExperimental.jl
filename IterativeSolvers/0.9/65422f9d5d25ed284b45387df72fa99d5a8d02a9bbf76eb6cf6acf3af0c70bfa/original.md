```
bicgstabl!(x, A, b, l; kwargs...) -> x, [history]
```

# Arguments

  * `A`: linear operator;
  * `b`: right hand side (vector);
  * `l::Int = 2`: Number of GMRES steps.

## Keywords

  * `max_mv_products::Int = size(A, 2)`: maximum number of matrix vector products.

For BiCGStab(l) this is a less dubious term than "number of iterations";

  * `Pl = Identity()`: left preconditioner of the method;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: absolute and relative tolerance for the stopping condition `|r_k| ≤ max(reltol * |r_0|, abstol)`, where `r_k ≈ A * x_k - b` is the approximate residual in the `k`th iteration;

    !!! note
        1. The true residual norm is never computed during the iterations, only an approximation;
        2. If a left preconditioner is given, the stopping condition is based on the *preconditioned residual*.

# Return values

**if `log` is `false`**

  * `x`: approximate solution.

**if `log` is `true`**

  * `x`: approximate solution;
  * `history`: convergence history.
