```
dof_residual(m::MixedModel)
```

Return the residual degrees of freedom of the model.

!!! note
    The residual degrees of freedom for mixed-effects models is not clearly defined due to partial pooling. The classical `nobs(m) - dof(m)` fails to capture the extra freedom granted by the random effects, but `nobs(m) - nranef(m)` would overestimate the freedom granted by the random effects. `nobs(m) - sum(leverage(m))` provides a nice balance based on the relative influence of each observation, but is computationally expensive for large models. This problem is also fundamentally related to [long-standing debates](https://bbolker.github.io/mixedmodels-misc/glmmFAQ.html#why-doesnt-lme4-display-denominator-degrees-of-freedomp-values-what-other-options-do-i-have) about the appropriate treatment of the denominator degrees of freedom for $F$-tests. In the future, MixedModels.jl may provide additional methods allowing the user to choose the computation to use.


!!! warning
    Currently, the residual degrees of freedom is computed as `nobs(m) - dof(m)`, but this may change in the future without being considered a breaking change because there is no canonical definition of the residual degrees of freedom in a mixed-effects model.

