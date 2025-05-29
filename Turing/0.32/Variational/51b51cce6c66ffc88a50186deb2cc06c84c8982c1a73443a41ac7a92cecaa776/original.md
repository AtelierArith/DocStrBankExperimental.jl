```
bijector(model::Model[, sym2ranges = Val(false)])
```

Returns a `Stacked <: Bijector` which maps from the support of the posterior to ℝᵈ with `d` denoting the dimensionality of the latent variables.
