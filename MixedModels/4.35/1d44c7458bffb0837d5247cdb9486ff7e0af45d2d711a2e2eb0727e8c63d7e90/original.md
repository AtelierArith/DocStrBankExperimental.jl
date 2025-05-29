```
likelihoodratiotest(m::MixedModel...)
likelihoodratiotest(m0::LinearModel, m::MixedModel...)
likelihoodratiotest(m0::GeneralizedLinearModel, m::MixedModel...)
likelihoodratiotest(m0::TableRegressionModel{LinearModel}, m::MixedModel...)
likelihoodratiotest(m0::TableRegressionModel{GeneralizedLinearModel}, m::MixedModel...)
```

Likeihood ratio test applied to a set of nested models.

!!! note
    The nesting of the models is not checked.  It is incumbent on the user to check this. This differs from `StatsModels.lrtest` as nesting in mixed models, especially in the random effects specification, may be non obvious.


!!! note
    For comparisons between mixed and non-mixed models, the deviance for the non-mixed model is taken to be -2 log likelihood, i.e. omitting the additive constant for the fully saturated model. This is in line with the computation of the deviance for mixed models.


This functionality may be deprecated in the future in favor of `StatsModels.lrtest`.
