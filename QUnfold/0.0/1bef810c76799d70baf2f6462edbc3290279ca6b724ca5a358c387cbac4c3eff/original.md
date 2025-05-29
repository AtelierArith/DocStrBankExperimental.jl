```
HDx(n_bins; kwargs...)
```

The Hellinger Distance-based method on feature histograms by González-Castro et al., 2013: *Class distribution estimation based on the Hellinger distance*.

The parameter `n_bins` specifies the number of bins *per feature*. A regularization strength `τ > 0` yields the o-HDx method for ordinal quantification, which is proposed by Bunse et al., 2022: *Machine learning for acquiring knowledge in astro-particle physics*.

**Keyword arguments**

  * `strategy = :softmax` is the solution strategy (see below).
  * `τ = 0.0` is the regularization strength for o-HDx.
  * `a = Float64[]` are the acceptance factors for unfolding analyses.

**Strategies**

González-Castro et al.'s loss function and feature transformation can be optimized with multiple strategies.

  * `:softmax` (default; our method) improves `:softmax_full_reg` by setting one latent parameter to zero instead of introducing a technical regularization term.
  * `:constrained` constrains the optimization to proper probability densities, as proposed by Hopkins & King, 2010: *A method of automated nonparametric content analysis for social science*.
  * `:softmax_full_reg` (our method) introduces a soft-max layer, which makes contraints obsolete. This strategy employs a technical regularization term, as proposed by Bunse, 2022: *On Multi-Class Extensions of Adjusted Classify and Count*.
  * `:softmax_reg` (our method) is a variant of `:softmax`, which sets one latent parameter to zero in addition to introducing a technical regularization term.
