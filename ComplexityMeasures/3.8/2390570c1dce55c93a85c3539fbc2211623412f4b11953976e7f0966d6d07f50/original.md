```
Shrinkage{<:OutcomeSpace} <: ProbabilitiesEstimator
Shrinkage(; t = nothing, λ = nothing)
```

The `Shrinkage` estimator is used with [`probabilities`](@ref) and related functions to estimate probabilities over the given `m`-element counting-based [`OutcomeSpace`](@ref) using James-Stein-type shrinkage [JamesStein1992](@cite), as presented in [Hausser2009](@citet).

## Description

The `Shrinkage` estimator estimates a cell probability $\theta_{k}^{\text{Shrink}}$ as

$$
\theta_{k}^{\text{Shrink}} = \lambda t_k + (1-\lambda) \hat{\theta}_k^{RelativeAmount},
$$

where $\lambda \in [0, 1]$ is the shrinkage intensity ($\lambda = 0$ means no shrinkage, and $\lambda = 1$ means full shrinkage), and $t_k$ is the shrinkage target. [Hausser2009](@citet) picks $t_k = 1/m$, i.e. the uniform distribution.

If `t == nothing`, then $t_k$ is set to $1/m$ for all $k$, as in [Hausser2009](@citet). If `λ == nothing` (the default), then the shrinkage intensity is optimized according to [Hausser2009](@citet). Hence, you should probably not pick `λ` nor `t` manually, unless you know what you are doing.

## Assumptions

The `Shrinkage` estimator assumes a fixed and known number of outcomes `m`. Thus, using it with [`probabilities_and_outcomes`](@ref)) and  [`allprobabilities_and_outcomes`](@ref) will yield different results, depending on whether all outcomes are observed in the input data or not. For [`probabilities_and_outcomes`](@ref), `m` is the number of *observed* outcomes. For [`allprobabilities_and_outcomes`](@ref), `m = total_outcomes(o, x)`, where `o` is the [`OutcomeSpace`](@ref) and `x` is the input data.

!!! note
    If used with [`allprobabilities_and_outcomes`](@ref), then outcomes which have not been observed may be assigned non-zero probabilities. This might affect your results if using e.g. [`missing_outcomes`](@ref).


## Examples

```julia
using ComplexityMeasures
x = cumsum(randn(100))
ps_shrink = probabilities(Shrinkage(), OrdinalPatterns{3}(), x)
```

See also: [`RelativeAmount`](@ref), [`BayesianRegularization`](@ref).
