```
prox_grad!(x, f, ∇f!, prox!; style=:noaccel, β=.5, ϵ=1e-7, max_iter=1000)
```

Minimize an objective function $f(x) + g(x)$, where $f(x)$ is differentibale while $g(x)$ is not, using the proximal gradient method. Storing the result in `x`. See also `prox_grad`.
