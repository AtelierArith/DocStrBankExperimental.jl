```
PhyloNetworkLinearModel <: GLM.LinPredModel
```

Phylogenetic linear model representation.

## Fields

`lm`, `V`, `Vy`, `RL`, `Y`, `X`, `logdetVy`, `reml`, `ind`, `nonmissing`, `evomodel`, `model_within` and `formula`. The following syntax pattern can be used to get more information on a specific field: e.g. to find out about the `lm` field, do `?PhyloNetworkLinearModel.lm`.

## Methods applied to fitted models

The following StatsAPI / StatsBase functions can be applied: `coef`, `nobs`, `vcov`, `stderror`, `confint`, `coeftable`, `dof_residual`, `dof`, `deviance`, `residuals`, `response`, `predict`, `loglikelihood`, `nulldeviance`, `nullloglikelihood`, `r2`, `adjr2`, `aic`, `aicc`, `bic`, `ftest`, `lrtest` etc.

The estimated variance-rate and estimated mean of the species-level trait model (see [`ContinuousTraitEM`](@ref)) can be retrieved using [`sigma2_phylo`](@ref) and [`mu_phylo`](@ref) respectively.

If relevant, the estimated individual-level/within-species variance can be retrieved using [`sigma2_within`](@ref).

The optimized λ parameter for Pagel's λ model (see [`PagelLambda`](@ref)) can be retrieved using [`lambda_estim`](@ref).

An ancestral state reconstruction can be performed using [`ancestralreconstruction`](@ref).

## Within-species variation

The true species/population means for the response trait/variable (or the residuals: conditional on the predictors) are jointly modeled as 𝒩(·, σ²ₛV) where V depends on the trait model (see [`ContinuousTraitEM`](@ref)) and on the species network. σ²ₛ is the between-species variance-rate.

Within-species variation is modeled by assuming that the individual-level responses are iid 𝒩(0, σ²ₑ) about the true species means, so that the species-level sample means (conditional on the predictors) are jointly modeled as 𝒩(·, σ²ₛV + σ²ₑD⁻¹), where σ²ₑ is the within-species variance and D⁻¹ is a diagonal matrix whose entries are the inverse sample-sizes (see [`WithinSpeciesCTM`](@ref)).

Although the above two models can be expressed in terms of a joint distribution for the species-level sample means (or residuals conditional on the predictors), more data are required to fit a model accounting for within-species variation, that is, a model recognizing that the sample means are estimates of the true population means. To fit a model *without* within-species variation, data on the species means are sufficient. To fit a model *with* within-species variation, we need to have the species means and the standard deviations of the response variable for each species.

`phylolm` can fit a model with within-species variation either from species-level statistics ("mean response" and "standard deviation in response") or from individual-level data (in which case the species-level statistics are computed internally). See [`phylolm`](@ref) for more details on these two input choices.

In the object, `obj.Y` and `obj.X` are the observed species means. `predict`, `residuals` and `response` return the values at the species level.
