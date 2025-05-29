```
phylolm(f::StatsModels.FormulaTerm, fr::AbstractDataFrame, net::HybridNetwork; kwargs...)
```

Fit a phylogenetic linear regression model to data. Return an object of type [`PhyloNetworkLinearModel`](@ref). It contains a linear model from the GLM package, in `object.lm`, of type [GLM.LinearModel](https://juliastats.org/GLM.jl/stable/api/#GLM.LinearModel).

## Arguments

  * `f`: formula to use for the regression, see [StatsModels](https://juliastats.org/StatsModels.jl/stable/)
  * `fr`: DataFrame containing the response values, predictor values, species/tip labels for each observation/row.
  * `net`: phylogenetic network to use. Should have labelled tips.

Keyword arguments

  * `model="BM"`: model for trait evolution (as a string) "lambda" (Pagel's lambda), "scalinghybrid" are other possible values (see [`ContinuousTraitEM`](@ref))
  * `tipnames=:tipnames`: column name for species/tip-labels, represented as a symbol. For example, if the column containing the species/tip labels in `fr` is named "Species", then do `tipnames=:Species`.
  * `no_names=false`: If `true`, force the function to ignore the tips names. The data is then assumed to be in the same order as the tips of the network. Default is false, setting it to true is dangerous, and strongly discouraged.
  * `reml=true`: if `true`, use REML criterion ("restricted maximum likelihood") for estimating variance components, else use ML criterion.
  * `suppresswarnings=false`: if `true`, PhyloTraits-specific warnings are suppressed. Currently, only Pagel's lambda model may throw a warning (if the network is not time-consistent).

The following tolerance parameters control the optimization of lambda if `model="lambda"` or `model="scalinghybrid"`, and control the optimization of the variance components if `model="BM"` and `withinspecies_var=true`.

  * `fTolRel=1e-10`: relative tolerance on the likelihood value
  * `fTolAbs=1e-10`: absolute tolerance on the likelihood value
  * `xTolRel=1e-10`: relative tolerance on the parameter value
  * `xTolAbs=1e-10`: absolute tolerance on the parameter value
  * `startingValue=0.5`: If `model`="lambda" or "scalinghybrid", this provides the starting value for the optimization in lambda.
  * `fixedValue=missing`: If `model`="lambda" or "scalinghybrid", and `fixedValue` is a number, then lambda is set to this number and is not optimized.
  * `withinspecies_var=false`: If `true`, fits a within-species variation model. Currently only implemented for `model`="BM".
  * `y_mean_std::Bool=false`: If `true`, and `withinspecies_var=true`, then accounts for within-species variation, using species-level statistics provided in `fr`.

## Methods applied to fitted models

To access the response values, do `response(object)`. To access the model matrix, do `modelmatrix(object)`. To access the model formula, do `formula(object)`.

## Within-species variation

For a high-level description, see [`PhyloNetworkLinearModel`](@ref). To fit a model with within-species variation in the response variable, either of the following must be provided in the data frame `fr`:

(1) Individual-level data: There should be columns for response, predictors, and species/tip-labels. Every row should correspond to an individual observation. At least one species must be represented by two or more individuals.

(2) Species-level statistics: There should be columns for mean response, predictors, species/tip-labels, species sample-sizes (number of individuals for each species), and species standard deviations (standard deviations of the response values by species). Every row should correspond to a species: each species should be represented by a unique row. The column names for species sample-sizes and species standard deviations are expected to be "[response column name]_n" and "[response column name]_sd". For example, if the response column name is "y", then the column names should be "y_n" and "y_sd" for the sample-sizes and standard deviations.

Regardless of whether the data provided follows (1) or (2), `withinspecies_var` should be set to true. If the data provided follows (2), then `y_mean_std` should be set to false.

## Within-species variation in predictors

The model assumes *no* within-species variation in predictors, because it aims to capture the evolutionary (historical, phylogenetic) relationship between the predictors and the response, not the within-species (present-day, or phenotypic) relationship.

If a within-species variation model is fitted on individual-level data, and if there are individuals within the same species with different values for the same predictor, these values are all replaced by the mean predictor value for all the individuals in that species. For example, suppose there are 3 individuals in a given species, and that their predictor values are (x₁=3, x₂=6), (x₁=4, x₂=8) and (x₁=2, x₂=1). Then the predictor values for these 3 individuals are each replaced by (x₁=(3+4+2)/3, x₂=(6+8+1)/3) before model fitting. If a fourth individual had data (x₁=10, x₂=missing), then that individual would be ignored for any model using x₂, and would not contribute any information to its species data for these models.

## Missing data

Rows with missing data for either the response or the predictors are omitted from the model-fitting. There should minimally be columns for response, predictors, species/tip-labels. As detailed above, additional columns may be required for fitting within-species variation. Missing data in the columns for species names, species standard deviation / sample sizes (if used) will throw an error.

## See also

[`rand`](@ref), [`ancestralreconstruction`](@ref), [`PhyloNetworks.vcv`](@extref)

## Examples: Without within-species variation

We first load data from the package and fit the default BM model.

```jldoctest phylolmdoc
julia> phy = readnewick(joinpath(dirname(pathof(PhyloTraits)), "..", "examples", "caudata_tree.txt"));

julia> using DataFrames, CSV # to read data file, next

julia> dat = CSV.read(joinpath(dirname(pathof(PhyloTraits)), "..", "examples", "caudata_trait.txt"), DataFrame);

julia> using StatsModels # for stat model formulas

julia> fitBM = phylolm(@formula(trait ~ 1), dat, phy; reml=false);

julia> fitBM # Shows a summary
PhyloNetworkLinearModel

Formula: trait ~ 1

Model: Brownian motion

Parameter Estimates, using ML:
phylogenetic variance rate: 0.00294521

Coefficients:
─────────────────────────────────────────────────────────────────────
             Coef.  Std. Error      t  Pr(>|t|)  Lower 95%  Upper 95%
─────────────────────────────────────────────────────────────────────
(Intercept)  4.679    0.330627  14.15    <1e-31    4.02696    5.33104
─────────────────────────────────────────────────────────────────────
Log Likelihood: -78.9611507833
AIC: 161.9223015666
```

We can extra parameters, likelihood, AIC etc.

```jldoctest phylolmdoc
julia> round(sigma2_phylo(fitBM), digits=6) # rounding for jldoctest convenience
0.002945

julia> round(mu_phylo(fitBM), digits=4)
4.679

julia> using StatsBase # for aic() stderror() loglikelihood() etc.

julia> round(loglikelihood(fitBM), digits=10)
-78.9611507833

julia> round(aic(fitBM), digits=10)
161.9223015666

julia> round(aicc(fitBM), digits=10)
161.9841572367

julia> round(bic(fitBM), digits=10)
168.4887090241

julia> round.(coef(fitBM), digits=4)
1-element Vector{Float64}:
 4.679

julia> confint(fitBM) # 95% (default) confidence interval for the coefficient(s)
1×2 Matrix{Float64}:
 4.02696  5.33104

julia> abs(round(r2(fitBM), digits=10)) # absolute value for jldoctest convenience
0.0

julia> abs(round(adjr2(fitBM), digits=10))
0.0

julia> round.(vcov(fitBM), digits=6) # variance-covariance of estimated parameters: squared standard error
1×1 Matrix{Float64}:
 0.109314
```

The residuals are the variance not explained by predictors. The phylogenetic correlation modelled by the BM is about them. The trait may have 2 sources of phylogenetic signal: from the predictor with which it the response may be associated, and from the residuals.

```jldoctest phylolmdoc
julia> round.(residuals(fitBM), digits=6)
197-element Vector{Float64}:
 -0.237648
 -0.357937
 -0.159387
 -0.691868
 -0.323977
 -0.270452
 -0.673486
 -0.584654
 -0.279882
 -0.302175
  ⋮
 -0.777026
 -0.385121
 -0.443444
 -0.327303
 -0.525953
 -0.673486
 -0.603158
 -0.211712
 -0.439833

julia> round.(response(fitBM), digits=5)
197-element Vector{Float64}:
 4.44135
 4.32106
 4.51961
 3.98713
 4.35502
 4.40855
 4.00551
 4.09434
 4.39912
 4.37682
 ⋮
 3.90197
 4.29388
 4.23555
 4.3517
 4.15305
 4.00551
 4.07584
 4.46729
 4.23917

julia> round.(predict(fitBM), digits=5)
197-element Vector{Float64}:
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 ⋮
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
 4.679
```

## Examples: With within-species variation (two different input formats shown)

We use a smaller network here. We can input data as 1 row per individual, multiple rows per species:

```jldoctest phylolmdoc
julia> net = readnewick("((((D:0.4,C:0.4):4.8,((A:0.8,B:0.8):2.2)#H1:2.2::0.7):4.0,(#H1:0::0.3,E:3.0):6.2):2.0,O:11.2);");

julia> df = DataFrame( # individual-level observations
           species = repeat(["D","C","A","B","E","O"],inner=3),
           trait1 = [4.08298,4.08298,4.08298,3.10782,3.10782,3.10782,2.17078,2.17078,2.17078,1.87333,1.87333,
              1.87333,2.8445,2.8445,2.8445,5.88204,5.88204,5.88204],
           trait2 = [-7.34186,-7.34186,-7.34186,-7.45085,-7.45085,-7.45085,-3.32538,-3.32538,-3.32538,-4.26472,
              -4.26472,-4.26472,-5.96857,-5.96857,-5.96857,-1.99388,-1.99388,-1.99388],
           trait3 = [18.8101,18.934,18.9438,17.0687,17.0639,17.0732,14.4818,14.1112,14.2817,13.0842,12.9562,
              12.9019,15.4373,15.4075,15.4317,24.2249,24.1449,24.1302]);

julia> m1 = phylolm(@formula(trait3 ~ trait1), df, net;
                    tipnames=:species, withinspecies_var=true)
PhyloNetworkLinearModel

Formula: trait3 ~ 1 + trait1

Model: Brownian motion

Parameter Estimates, using REML:
phylogenetic variance rate: 0.156188
within-species variance: 0.0086343

Coefficients:
──────────────────────────────────────────────────────────────────────
               Coef.  Std. Error     t  Pr(>|t|)  Lower 95%  Upper 95%
──────────────────────────────────────────────────────────────────────
(Intercept)  9.65347    1.3066    7.39    0.0018    6.02577   13.2812
trait1       2.30358    0.276163  8.34    0.0011    1.53683    3.07033
──────────────────────────────────────────────────────────────────────
Log Likelihood: 1.9446255188
AIC: 4.1107489623
```

Alternatively, we can input the data as 1 row per species and 2 extra columns: standard deviation of the response trait among individuals in the same species, and number of individuals per species for which we calculated this SD. The result is the same.

```jldoctest phylolmdoc
julia> df_r = DataFrame( # species-level statistics (sample means, standard deviations)
           species = ["D","C","A","B","E","O"],
           trait1 = [4.08298,3.10782,2.17078,1.87333,2.8445,5.88204],
           trait2 = [-7.34186,-7.45085,-3.32538,-4.26472,-5.96857,-1.99388],
           trait3 = [18.896,17.0686,14.2916,12.9808,15.4255,24.1667],
           trait3_sd = [0.074524,0.00465081,0.185497,0.0936,0.0158379,0.0509643],
           trait3_n = [3, 3, 3, 3, 3, 3]);

julia> m2 = phylolm(@formula(trait3 ~ trait1), df_r, net;
                tipnames=:species, withinspecies_var=true, y_mean_std=true)
PhyloNetworkLinearModel

Formula: trait3 ~ 1 + trait1

Model: Brownian motion

Parameter Estimates, using REML:
phylogenetic variance rate: 0.15618
within-species variance: 0.0086343

Coefficients:
──────────────────────────────────────────────────────────────────────
               Coef.  Std. Error     t  Pr(>|t|)  Lower 95%  Upper 95%
──────────────────────────────────────────────────────────────────────
(Intercept)  9.65342    1.30657   7.39    0.0018    6.02582   13.281
trait1       2.30359    0.276156  8.34    0.0011    1.53686    3.07032
──────────────────────────────────────────────────────────────────────
Log Likelihood: 1.9447243714
AIC: 4.1105512573
```
