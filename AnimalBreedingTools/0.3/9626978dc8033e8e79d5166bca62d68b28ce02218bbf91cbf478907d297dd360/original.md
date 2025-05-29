```
x = solve_pcg(A,b; maxiter=5000,eps=1e-15,reset=50,verbose=false)
```

Solve the symmetric positive definite system of equations: `A` as sparse left-hand side and `b` as a vector of right-hand side. The Jacobi preconditioner (`diag(A)`) is used. The maximum number of iterations is specified with `maxiter`. Convergence criterion `eps` is `norm(b-A*x)/norm(b)`. The residual vector will be recalculated every `reset` rounds. The details will be shown with `verbose=true`.

```juliadoctest
julia> x = solve_pcg(A,b)
```
