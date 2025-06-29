```
MissingDispersionPatterns <: ComplexityEstimator
MissingDispersionPatterns(o = Dispersion()) → mdp
```

An estimator for the number of missing dispersion patterns (MDP), a complexity measure which can be used to detect nonlinearity in time series [Zhou2023](@cite).

Used with [`complexity`](@ref) or [`complexity_normalized`](@ref).

## Description

When used with [`complexity`](@ref), `complexity(mdp)` is syntactically equivalent with just [`missing_outcomes`](@ref)`(o)`. When used with [`complexity_normalized`](@ref), the normalization is simply `missing_outcomes(o)/total_outcomes(o)`.

!!! note "Encoding"
    [`Dispersion`](@ref)'s linear mapping from CDFs to integers is based on equidistant partitioning of the interval `[0, 1]`. This is slightly different from [Zhou2023](@citet), which uses the linear mapping $s_i := \text{round}(y + 0.5)$.


## Usage

In [Zhou2023](@citet), [`MissingDispersionPatterns`](@ref) is used to detect nonlinearity in time series by comparing the MDP for a time series `x` to values for an ensemble of surrogates of `x`, as per the standard analysis of [TimeseriesSurrogates.jl](https://github.com/JuliaDynamics/TimeseriesSurrogates.jl) If the MDP value of $x$ is significantly larger than some high quantile of the surrogate distribution, then it is taken as evidence for nonlinearity.

See also: [`Dispersion`](@ref), [`ReverseDispersion`](@ref), [`total_outcomes`](@ref).
