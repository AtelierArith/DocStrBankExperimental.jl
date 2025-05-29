```
X = hulyapc!(U, Q; adj = false)
```

Compute for an upper triangular `U` and a hermitian `Q` an upper triangular solution `X` of the continuous H-Lyapunov matrix equation

```
            U'*X + X'*U = Q   if adj = false,
```

or

```
            U*X' + X*U' = Q   if adj = true.
```

The solution `X` overwrites the matrix `Q`, while `U` is unchanged.

If `U` is nonsingular, a backward elimination method is used, if `adj = false`, or a forward elimination method is used if `adj = true`, by adapting the approach  employed in the function `dU_from_dQ!` of the [`DiffOpt.jl`](https://github.com/jump-dev/DiffOpt.jl) package.  For a `n×n`  singular `U`, a least-squares upper-triangular solution `X` is determined using a conjugate-gradient based iterative method applied  to a suitably defined T-Lyapunov linear operator `L:X -> Y`, which maps upper triangular matrices `X` into upper triangular matrices `Y`, and the associated matrix `M = Matrix(L)` is $n(n+1)/2 \times n(n+1)/2$.  In this case, the keyword argument `tol` (default: `tol = sqrt(eps())`) can be used to provide the desired tolerance for the accuracy of the computed solution and  the keyword argument `maxiter` can be used to set the maximum number of iterations (default: maxiter = 1000). 
