```
nonparametricbootstrap([rng::AbstractRNG,] nsamp::Integer, m::LinearMixedModel;
                       use_threads=false, blup_method=ranef, β=coef(morig))
```

Perform `nsamp` nonparametric bootstrap replication fits of `m`, returning a `MixedModelBootstrap`.

The default random number generator is `Random.GLOBAL_RNG`.

`GeneralizedLinearMixedModel` is currently unsupported.

# Named Arguments

`progress=false` can be used to disable the progress bar. Note that the progress bar is automatically disabled for non-interactive (i.e. logging) contexts.

`blup_method` provides options for how/which group-level effects are passed for resampling. The default `ranef` uses the shrunken conditional modes / BLUPs. Unshrunken estimates from ordinary least squares (OLS) can be used with `olsranef`. There is no shrinkage of the group-level estimates with this approach, which means singular estimates can be avoided. However, if the design matrix for the random effects is rank deficient (e.g., through the use of `MixedModels.fulldummy` or missing cells in the data), then this method will fail. See [`olsranef`](@ref) and `MixedModels.ranef` for more information.

`residual_method` provides options for how observation-level residuals are passed for permutation. This should be a two-argument function, taking the model and the BLUPs (as computed with `blup_method`) as arguments. If you wish to ignore the BLUPs as computed with `blup_method`, then you still need the second argument, but you can simply not use it in your function.

`inflation_method` is a three-argument function (model, BLUPs as computed by `blup_method`, residuals computed by `residual_method`) for computing the inflation factor passed onto [`resample!`](@ref).

# Method

The method implemented here is based on the approach given in Section 3.2 of: Carpenter, J.R., Goldstein, H. and Rasbash, J. (2003). A novel bootstrap procedure for assessing the relationship between class size and achievement. Journal of the Royal Statistical Society: Series C (Applied Statistics), 52: 431-443. https://doi.org/10.1111/1467-9876.00415
