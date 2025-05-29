```
treeverse(f, gf, s; δ, N, τ=binomial_fit(N,δ), f_inplace=true, logger = TreeverseLog())
```

Treeverse algorithm for back-propagating a program memory efficiently.

Positional arguments

  * `f`, the step function that $s_{i+1} = f(s_i)$,
  * `gf`, the single step gradient function that $g_i = gf(s_i, g_{i+1})$. When $g_{i+1}$ is `nothing`, it should return the gradient passed from the later step.
  * `s`, the initial state $s_0$,

Keyword arguments

  * `δ`, the number of checkpoints,
  * `N`, the number of time steps,
  * `τ`, the number of sweeps, it is chosen as the smallest integer that `binomial(τ+δ, τ) >= N` by default,
  * `f_inplace = false`, whether `f` is inplace,
  * `logger = TreeverseLog()`, the logger.

Ref: https://www.tandfonline.com/doi/abs/10.1080/10556789208805505
