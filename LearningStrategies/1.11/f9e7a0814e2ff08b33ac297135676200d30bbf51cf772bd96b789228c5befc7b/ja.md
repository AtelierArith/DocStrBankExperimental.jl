```
Converged(f; tol = 1e-6, every = 1)
```

`norm(f(model) - lastf) ≦ tol` のときに学習を停止します。 `f` は `Vector{Float64}` を返さなければなりません。
