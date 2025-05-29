```
LatentGP(f<:AbstractGP, lik, Σy)
```

  * `f` is a `AbstractGP`.
  * `lik` is the likelihood function which maps samples from `f` to the corresponding conditional likelihood distributions (i.e., `lik` must return a `Distribution` compatible with the observations).
  * `Σy` is the noise under which the latent GP is "observed"; this represents the jitter used to avoid numeric instability and should generally be small.
