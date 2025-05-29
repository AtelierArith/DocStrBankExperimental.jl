```
likelihood_ratio(ℓ::Likelihood, p, q)
```

Compute the log of the likelihood ratio, in order to compare two choices for parameters. This is equal to

```
density_rel(ℓ.k(p), ℓ.k(q), ℓ.x)
```

but is computed using LogarithmicNumbers.jl to avoid underflow and overflow. Since `density_rel` can leave common base measure unevaluated, this can be more efficient than

```
logdensityof(ℓ.k(p), ℓ.x) - logdensityof(ℓ.k(q), ℓ.x)
```
