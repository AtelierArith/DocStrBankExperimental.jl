```
SLD(classifier; kwargs...)
```

The Saerens-Latinne-Decaestecker method, a.k.a. EMQ or Expectation Maximization-based Quantification by Saerens et al., 2002: *Adjusting the outputs of a classifier to new a priori probabilities: A simple procedure*.

A polynomial order `o > 0` and regularization impact `λ > 0` yield the o-SLD method for ordinal quantification, which is proposed by Bunse et al., 2022: *Machine learning for acquiring knowledge in astro-particle physics*.

**Keyword arguments**

  * `o = 0` is the order of the polynomial for o-SLD.
  * `λ = 0.0` is the impact of the polynomial for o-SLD.
  * `a = Float64[]` are the acceptance factors for unfolding analyses.
  * `fit_classifier = true` whether or not to fit the given `classifier`.
