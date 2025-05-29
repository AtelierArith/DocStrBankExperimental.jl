```
quadgk_count(f, args...; kws...)
```

Identical to [`quadgk`](@ref) but returns a triple `(I, E, count)` of the estimated integral `I`, the estimated error bound `E`, and a `count` of the number of times the integrand `f` was evaluated.

The count of integrand evaluations is a useful performance metric: a large number typically indicates a badly behaved integrand (with singularities, discontinuities, sharp peaks, and/or rapid oscillations), in which case it may be possible to mathematically transform the problem in some way to improve the convergence rate.
