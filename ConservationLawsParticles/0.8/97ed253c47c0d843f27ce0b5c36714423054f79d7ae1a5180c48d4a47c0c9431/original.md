```
integrated_interaction([t,] x, W, ys[, dens_diff])
```

Computes $-(W' * \rho)(t, x) = -(W * \rho')(t,x)$, where $\rho$ is the piecewise-constant density associated to the particles `ys`.

It `t` is omitted, then `W(x)` is assumed independent of time.

!!! note
    To ensure the correctness of the computation, `dens_diff` must coincide with `diff(pwc_density(ys))`. It can be pre-computed and passed explicitly to allow reuse (as an optimization).


See also [`sampled_interaction`](@ref), [`compute_interaction`](@ref).
