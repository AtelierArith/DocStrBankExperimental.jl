```
Solver(program, kktsolve, η, γ)
```

Constructs a new QP solver object.

# Parameters:

  * `program`: The QP to solve
  * `kktsolve`: The function to solve the KKT system
  * `η`: Optimization parameter typically set to zero or σ, default is 0.0
  * `γ`: Mehrotra correction parameter set to γ ∈ [0, 1], default is 1.0

NOTE: Set η as nothing to set to σ.
