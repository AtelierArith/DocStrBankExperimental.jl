```
MixedModel
```

Abstract type for mixed models.  MixedModels.jl implements two subtypes: `LinearMixedModel` and `GeneralizedLinearMixedModel`.  See the documentation for each for more details.

This type is primarily used for dispatch in `fit`.  Without a distribution and link function specified, a `LinearMixedModel` will be fit.  When a distribution/link function is provided, a `GeneralizedLinearModel` is fit, unless that distribution is `Normal` and the link is `IdentityLink`, in which case the resulting GLMM would be equivalent to a `LinearMixedModel` anyway and so the simpler, equivalent `LinearMixedModel` will be fit instead.
