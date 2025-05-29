```
IBU(transformer, n_bins; kwargs...)
```

The Iterative Bayesian Unfolding method by D'Agostini, 1995: *A multidimensional unfolding method based on Bayes' theorem*.

**Keyword arguments**

  * `o = 0` is the order of the polynomial for ordinal quantification.
  * `λ = 0.0` is the impact of the polynomial for ordinal quantification.
  * `a = Float64[]` are the acceptance factors for unfolding analyses.
