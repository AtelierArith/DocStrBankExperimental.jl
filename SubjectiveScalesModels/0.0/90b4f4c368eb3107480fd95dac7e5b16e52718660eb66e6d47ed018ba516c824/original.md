```
OrderedBeta(μ, ϕ, k0, k1)
```

This distribution was introduced by [Kubinec (2023)](https://doi.org/10.1017/pan.2022.20) as an appropriate and parsimonious way of describing data commonly observed in psychological science (such as from slider scales).  It is defined with a Beta distribution on the interval ]0, 1[ with additional point masses at 0 and 1. The Beta distribution is specified using the [`BetaPhi2`](@ref) parametrization.

# Arguments

  * `μ`: location parameter on the scale 0-1
  * `ϕ`: precision parameter (must be positive). Note that this parameter is based on the [`BetaPhi2`](@ref) reparametrization of the Beta distribution,   which corresponds to half the precision of the traditional Beta distribution as implemented in for example the `ordbetareg` package.
  * `k0`: first cutpoint beyond which the probability of zeros increases. Likely lower than 0.5 (also referred to as `cutzero` in the ordbetareg and *k1* in the paper).
  * `k1`: second cutpoint beyond which the probability of ones increases. Likely higher than 0.5. Must be greater than `k0` (also referred to as `cutone` in the ordbetareg and *k2* in the paper).

Note that when `k0=0` and `k1=1`, the distribution is equivalent to a Beta distribution (i.e., there are no zeros or ones).

# Details

![](https://github.com/DominiqueMakowski/SubjectiveScalesModels.jl/blob/main/docs/img/animation_OrderedBeta.gif?raw=true)

The figure above shows the parameter space for *k0* and *k1*, showing the regions that produce a large proportion of zeros and ones (in red). Understanding this is important to set appropriate priors on these parameters.

Compared to the `ordbetareg` R package, the main difference is that:

  * *phi* ϕ (Julia version) = *phi* ϕ (R version) / 2
  * *k0* and *k1* are specified on the raw scale [0, 1], and independently (in the R package, they are specified on the logit scale and k1 is expressed as a difference from k0).

# Examples

```jldoctest
julia> OrderedBeta(0.5, 1, 0.1, 0.9)
OrderedBeta{Float64}(μ=0.5, ϕ=1.0, k0=0.1, k1=0.9)
```

# References

  * Kubinec, R. (2023). Ordered beta regression: a parsimonious, well-fitting model for continuous data with lower and upper bounds. Political analysis, 31(4), 519-536.
