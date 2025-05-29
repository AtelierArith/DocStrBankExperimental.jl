```
RUN(transformer; kwargs...)
```

The Regularized Unfolding method by Blobel, 1985: *Unfolding methods in high-energy physics experiments*.

**Keyword arguments**

  * `strategy = :softmax` is the solution strategy (see below).
  * `τ = 1e-6` is the regularization strength for ordinal quantification.
  * `n_df = -1` (only used if `strategy==:original`) is the effective number of degrees of freedom, required to be `0 < n_df <= C` where `C` is the number of classes.
  * `a = Float64[]` are the acceptance factors for unfolding analyses.

**Strategies**

Blobel's loss function, feature transformation, and regularization can be optimized with multiple strategies.

  * `:softmax` (default; our method) improves `:softmax_full_reg` by setting one latent parameter to zero instead of introducing a technical regularization term.
  * `:original` is the original, unconstrained Newton optimization proposed by Blobel (1985).
  * `:constrained` constrains the optimization to proper probability densities, as proposed by Hopkins & King, 2010: *A method of automated nonparametric content analysis for social science*.
  * `:softmax_full_reg` (our method) introduces a soft-max layer, which makes contraints obsolete. This strategy employs a technical regularization term, as proposed by Bunse, 2022: *On Multi-Class Extensions of Adjusted Classify and Count*.
  * `:softmax_reg` (our method) is a variant of `:softmax`, which sets one latent parameter to zero in addition to introducing a technical regularization term.
  * `:unconstrained` (our method) is similar to `:original`, but uses a more generic solver.
