```
icc(model::MixedModel, [groups])
icc(boot::MixedModelBootstrap, [family], [groups])
```

Compute the intra-class correlation coefficient (ICC) for a mixed model.

The ICC is defined as the variance attributable to the `groups` divided by the total variance from all groups and the observation-level (residual) variance. In other words, the ICC can be interpreted as the proportion of the variance explainable by the grouping/nesting structure.

A single `group` can be specified as a Symbol, e.g. `:subj` or a number of groups can be specified as an array: `[:subj, :item]`. If no `groups` are specified, then all grouping variables are used.

When a `MixedModelBootstrap` is passed, a vector of ICC values for each bootstrap iteration is returned. Because `MixedModelBootstrap` does not store the associated model family for generalized linear mixed models, the family must be specified (e.g., `Bernoulli()`, `Poisson()`). A shortest coverage interval can be computed with `MixedModels.shortestcovint`.

!!! note
    The value returned here is sometimes called the "adjusted ICC" and does not take the variance of the fixed effects into account (the "conditional ICC").


!!! note
    The result returned aggregates across groups. If you require the ICC for each group separately, then you must call `icc` separately for each group.

