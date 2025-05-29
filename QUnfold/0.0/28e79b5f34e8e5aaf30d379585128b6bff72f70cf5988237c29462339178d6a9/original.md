```
PACC(classifier; kwargs...)
```

The Probabilistic Adjusted Classify & Count method, which solves a least squares objective with predictions of posterior probabilities.

A regularization strength `τ > 0` yields the o-PACC method for ordinal quantification, which is proposed by Bunse et al., 2022: *Ordinal Quantification through Regularization*.

**Keyword arguments**

  * `strategy = :softmax` is the solution strategy (see below).
  * `τ = 0.0` is the regularization strength for o-PACC.
  * `a = Float64[]` are the acceptance factors for unfolding analyses.
  * `fit_classifier = true` whether or not to fit the given `classifier`.

**Strategies**

For binary classification, PACC is proposed by Bella et al., 2010: *Quantification via Probability Estimators*. In the multi-class setting, multiple extensions are available.

  * `:softmax` (default; our method) improves `:softmax_full_reg` by setting one latent parameter to zero instead of introducing a technical regularization term.
  * `:constrained` constrains the optimization to proper probability densities, as proposed by Hopkins & King, 2010: *A method of automated nonparametric content analysis for social science*.
  * `:pinv` computes a pseudo-inverse akin to a minimum-norm constraint, as discussed by Bunse, 2022: *On Multi-Class Extensions of Adjusted Classify and Count*.
  * `:inv` computes the true inverse (if existent) of the transfer matrix `M`, as proposed by Vucetic & Obradovic, 2001: *Classification on data with biased class distribution*.
  * `:ovr` solves multiple binary one-versus-rest adjustments, as proposed by Forman (2008).
  * `:none` yields the `CC` method without any adjustment.
  * `:softmax_full_reg` (our method) introduces a soft-max layer, which makes contraints obsolete. This strategy employs a technical regularization term, as proposed by Bunse, 2022: *On Multi-Class Extensions of Adjusted Classify and Count*.
  * `:softmax_reg` (our method) is a variant of `:softmax`, which sets one latent parameter to zero in addition to introducing a technical regularization term.
