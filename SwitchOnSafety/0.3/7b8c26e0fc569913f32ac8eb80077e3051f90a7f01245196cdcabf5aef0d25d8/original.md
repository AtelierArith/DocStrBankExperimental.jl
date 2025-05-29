```
gripenberg(s::AbstractDiscreteSwitchedSystem; δ=1e-2,
                max_eval = 10000, max_ρ_eval = max_eval,
                max_norm_eval = max_eval, max_length = 50,
                matrix_norm = A -> opnorm(A, 2), verbose = 1)
```

Gripenberg algorithm [G96] for computing an upper bound `ub` and a lower bound `lb` to the Joint Spectral Radius such that `ub - lb ≤ 1e-2`.

[G96] Gripenberg, G. Computing the joint spectral radius. *Linear Algebra and its Applications*, *Elsevier*, **1996**, *234*, 43-60
