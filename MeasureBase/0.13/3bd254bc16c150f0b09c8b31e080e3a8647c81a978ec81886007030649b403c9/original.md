```
log_likelihood_ratio(ℓ::Likelihood, p, q)
```

Compute the log of the likelihood ratio, in order to compare two choices for parameters. This is computed as

```
logdensity_rel(ℓ.k(p), ℓ.k(q), ℓ.x)
```

Since `logdensity_rel` can leave common base measure unevaluated, this can be more efficient than

```
logdensityof(ℓ.k(p), ℓ.x) - logdensityof(ℓ.k(q), ℓ.x)
```
