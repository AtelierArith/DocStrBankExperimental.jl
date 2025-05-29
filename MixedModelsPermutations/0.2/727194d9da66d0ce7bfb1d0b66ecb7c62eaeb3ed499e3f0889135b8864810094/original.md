```
permutation([rng::AbstractRNG,] nsamp::Integer, m::LinearMixedModel;
            use_threads::Bool=false,
            β=zeros(length(coef(morig))),
            residual_permutation=:signflip,
            blup_method=ranef,
            residual_method=residuals)
```

Perform `nsamp` nonparametric bootstrap replication fits of `m`, returning a `MixedModelBootstrap`.

The default random number generator is `Random.GLOBAL_RNG`.

`GeneralizedLinearMixedModel` is currently unsupported.

# Named Arguments

`progress=false` can be used to disable the progress bar. Note that the progress bar is automatically disabled for non-interactive (i.e. logging) contexts.

Permutation at the level of residuals can be accomplished either via sign flipping (`residual_permutation=:signflip`) or via classical permutation/shuffling (`residual_permutation=:shuffle`).

`blup_method` provides options for how/which group-level effects are passed for permutation. The default `ranef` uses the shrunken conditional modes / BLUPs. Unshrunken estimates from ordinary least squares (OLS) can be used with `olsranef`. There is no shrinkage of the group-level estimates with this approach, which means singular estimates can be avoided. However, if the design matrix for the random effects is rank deficient (e.g., through the use of `MixedModels.fulldummy` or missing cells in the data), then this method will fail. See [`olsranef`](@ref) and `MixedModels.ranef` for more information.

`residual_method` provides options for how observation-level residuals are passed for permutation. This should be a two-argument function, taking the model and the BLUPs (as computed with `blup_method`) as arguments. If you wish to ignore the BLUPs as computed with `blup_method`, then you still need the second argument, but you can simply not use it in your function.

`inflation_method` is a three-argument function (model, BLUPs as computed by `blup_method`, residuals computed by `residual_method`) for computing the inflation factor passed onto [`permute!`](@ref).

Generally, permutations are used to test a particular (null) hypothesis. This hypothesis is specified via by setting `β` argument to match the hypothesis. For example, the null hypothesis that the first coefficient is zero would expressed as

```julialang
julia> hypothesis = coef(model);
julia> hypothesis[1] = 0.0;
```

!!! note
    The permutation (test) generates samples from H0, from which it is possible to compute p-values. The bootstrap typically generates samples from H1, which are convenient for generating coverage/confidence intervals. Of course, confidence intervals and p-values are duals of each other, so it is possible to convert from one to the other.


# Method

The method implemented here is based on the approach given in:

ter Braak C.J.F. (1992) Permutation Versus Bootstrap Significance Tests in Multiple Regression and Anova. In: Jöckel KH., Rothe G., Sendler W. (eds) Bootstrapping and Related Techniques. Lecture Notes in Economics and Mathematical Systems, vol 376. Springer, Berlin, Heidelberg. https://doi.org/10.1007/978-3-642-48850-4_10

and

Winkler, A. M., Ridgway, G. R., Webster, M. A., Smith, S. M., & Nichols, T. E. (2014). Permutation inference for the general linear model. NeuroImage, 92, 381–397. https://doi.org/10.1016/j.neuroimage.2014.01.060

!!! warning
    This method has serious limitations for singular models because sign-flipping a zero is not an effective randomization technique.

