```
gripenberg(s::AbstractDiscreteSwitchedSystem; δ=1e-2,
                max_eval = 10000, max_ρ_eval = max_eval,
                max_norm_eval = max_eval, max_length = 50,
                matrix_norm = A -> opnorm(A, 2), verbose = 1)
```

Gripenbergアルゴリズム [G96] は、上限 `ub` と下限 `lb` を計算するためのものであり、Joint Spectral Radiusに対して `ub - lb ≤ 1e-2` となるようにします。

[G96] Gripenberg, G. Computing the joint spectral radius. *Linear Algebra and its Applications*, *Elsevier*, **1996**, *234*, 43-60
