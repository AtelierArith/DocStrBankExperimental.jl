```
olsranef(model::LinearMixedModel, method=:simultaneous)
```

Compute the group-level estimates using ordinary least squares.

This is somewhat similar to the conditional modes / BLUPs computed without shrinkage.

There is no shrinkage of the group-level estimates with this approach, which means singular estimates can be avoided. However, this also means the random effects design matrix must not be singular.

The following methods are provided:

1. (default) OLS estimates computed for all strata (blocking variables) simultaneously with `method=:simultaneous`. This pools the variance across estimates but does not shrink the estimates. Note that this method internal reparameterizes the random effects matrix `Z` to use effects coding and only use a single intercept shared across all grouping variables.
2. OLS estimates computed within each stratum with `method=:stratum`. This method is equivalent for example to computing each subject-level and each item-level regression separately.
3. Pseudo-OLS estimated computed by applying extremely mild shrinkage to achieve essentially unpenalized conditional (i.e. within group) means with `method=:inflated_identity`. This method is also used in MixedModelsMakie for generating shrinkage plots

For fully balanced designs with a single blocking variable, these methods will give the same results.

!!! warning
    If the design matrix for the random effects is rank deficient (e.g., through the use of `MixedModels.fulldummy` or missing cells in the data), then the methods `:simultaneous` and `:stratum` will fail because no shrinkage/regularization is applied.

