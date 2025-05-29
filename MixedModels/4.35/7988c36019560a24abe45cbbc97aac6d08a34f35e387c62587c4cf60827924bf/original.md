```
fit!(m::GeneralizedLinearMixedModel; fast=false, nAGQ=1,
                                     verbose=false, progress=true,
                                     thin::Int=1,
                                     init_from_lmm=Set())
```

Optimize the objective function for `m`.

When `fast` is `true` a potentially much faster but slightly less accurate algorithm, in which `pirls!` optimizes both the random effects and the fixed-effects parameters, is used.

If `progress` is `true`, the default, a `ProgressMeter.ProgressUnknown` counter is displayed. during the iterations to minimize the deviance.  There is a delay before this display is initialized and it may not be shown at all for models that are optimized quickly.

If `verbose` is `true`, then both the intermediate results of both the nonlinear optimization and PIRLS are also displayed on standard output.

The `thin` argument is ignored: it had no impact on the final model fit and the logic around thinning the `fitlog` was needlessly complicated for a trivial performance gain.

By default, the starting values for model fitting are taken from a (non mixed, i.e. marginal ) GLM fit. Experience with larger datasets (many thousands of observations and/or hundreds of levels of the grouping variables) has suggested that fitting a (Gaussian) linear mixed model on the untransformed data may provide better starting values and thus overall faster fits even though an entire LMM must be fit before the GLMM can be fit. `init_from_lmm` can be used to specify which starting values from an LMM to use. Valid options are any collection (array, set, etc.) containing one or more of `:β` and `:θ`, the default is the empty set.

!!! note
    Initializing from an LMM requires fitting the entire LMM first, so when `progress=true`, there will be two progress bars: first for the LMM, then for the GLMM.


!!! warning
    The `init_from_lmm` functionality is experimental and may change or be removed entirely without being considered a breaking change.

