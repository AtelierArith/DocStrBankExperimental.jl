```
sampled_interaction([t,] x, W′, ys)
```

Computes $-(W' * \dot\rho)(t, x)$, which is the sampled approximation of $-(W' * \rho)(t, x)$, where $\rho$ is the piecewise-constant density associated to the particles `ys`.

It `t` is omitted, then `W′(x)` is assumed independent of time.

See also [`integrated_interaction`](@ref), [`compute_interaction`](@ref).
