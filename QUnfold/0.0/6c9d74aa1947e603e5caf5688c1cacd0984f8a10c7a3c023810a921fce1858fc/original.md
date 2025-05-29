```
TreeTransformer(tree; kwargs...)
```

This transformer yields a tree-induced partitioning, as proposed by Börner et al., 2017: *Measurement/simulation mismatches and multivariate data discretization in the machine learning era*.

**Keyword arguments**

  * `fit_frac = 1/5` is the fraction of data used for training the tree if `fit_tree==true`.
  * `fit_tree = true` whether or not to fit the given `tree`.
