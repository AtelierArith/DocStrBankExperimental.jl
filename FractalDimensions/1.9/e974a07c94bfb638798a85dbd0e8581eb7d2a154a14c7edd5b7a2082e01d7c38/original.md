```
extremevaltheory_gpdfit_pvalues(X, p; kw...)
```

Return various computed quantities that may quantify the significance of the results of [`extremevaltheory_dims_persistences`](@ref)`(X, p; kw...)`, terms of quantifying how well a Generalized Pareto Distribution (GPD) describes exceedences in the input data.

## Keyword arguments

  * `show_progress = true`: display a progress bar.
  * `TestType = ApproximateOneSampleKSTest`: the test type to use. It can be `ApproximateOneSampleKSTest, ExactOneSampleKSTest, CramerVonMises`. We noticed that `OneSampleADTest` sometimes yielded nonsensical results: all p-values were equal and were very small ≈ 1e-6.
  * `nbins = round(Int, length(X)*(1-p)/20)`: number of bins to use when computing the histogram of the exceedances for computing the NRMSE. The default value will use equally spaced bins that are equal to the length of the exceedances divided by 20.

## Description

The function computes the exceedances $E_i$ for each point $x_i \in X$ as in [`extremevaltheory_dims_persistences`](@ref). It returns 5 quantities, all being vectors of length `length(X)`:

  * `Es`, all exceedences, as a vector of vectors.
  * `sigmas, xis` the fitted σ, ξ to the GPD fits for each exceedance
  * `nrmses` the normalized root mean square distance of the fitted GPD to the histogram of the exceedances
  * `pvalues` the pvalues of a statistical test of the appropriateness of the GPD fit

The output `nrmses` quantifies the distance between the fitted GPD and the empirical histogram of the exceedances. It is computed as

$$
NRMSE = \sqrt{\frac{\sum{(P_j - G_j)^2}{\sum{(P_j - U)^2}}
$$

where $P_j$ the empirical (observed) probability at bin $j$, $G_j$ the fitted GPD probability at the midpoint of bin $j$, and $U$ same as $G_j$ but for the uniform distribution. The divisor of the equation normalizes the expression, so that the error of the empirical distribution is normalized to the error of the empirical distribution with fitting it with the uniform distribution. It is expected that NRMSE < 1. The smaller it is, the better the data are approximated by GPD versus uniform distribution.

The output `pvalues` is a vector of p-values. `pvalues[i]` corresponds to the p-value of the hypothesis: *"The exceedences around point `X[i]` are sampled from a GPD"* versus the alternative hypothesis that they are not. To extract the p-values, we perform a one-sample hypothesis via HypothesisTests.jl to the fitted GPD. Very small p-values then indicate that the hypothesis should be rejected and the data are not well described by a GPD. This can be an indication that we do not have enough data, or that we choose too high of a quantile probability `p`, or that the data are not suitable in general. This p-value based method for significance has been used in [^Faranda2017], but it is unclear precisely how it was used.

For more details on how these quantities may quantify significance, see our review paper.

[^Faranda2017]: Faranda et al. (2017), Dynamical proxies of North Atlantic predictability and extremes, [Scientific Reports, 7](https://doi.org/10.1038/srep41278)
