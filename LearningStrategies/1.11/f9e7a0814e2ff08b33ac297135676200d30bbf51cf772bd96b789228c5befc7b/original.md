```
Converged(f; tol = 1e-6, every = 1)
```

Stop learning when `norm(f(model) - lastf) ≦ tol`.  `f` must return a `Vector{Float64}`.
