```
EconometricModel(estimator::Type{<:Union{EconometricModel,ModelEstimator}},
                 f::FormulaTerm,
                 data;
                 contrasts::Dict{Symbol} = Dict{Symbol,Union{<:AbstractContrasts,<:AbstractTerm}}(),
                 wts::Union{Nothing,Symbol} = nothing,
                 panel::Union{Nothing,Symbol} = nothing,
                 time::Union{Nothing,Symbol} = nothing,
                 vce::VCE = OIM)
```

Formula has syntax:

```
@formula(response ~ exogenous + (endogenous ~ instruments) + absorb(highdimscontrols))
```

Data must implement the Tables.jl API and use CategoricalArrays (CategoricalVector)

Weights are taken as `StatsBase.FrequencyWeights`

Panel and time indicators are used for longitudinal estimators

# Examples

```
model = fit(EconometricModel, formula, data, kwargs...)
model = fit(BetweenEstimator, formula, data, panel = :panel, kwargs...)
model = fit(RandomEffectsEstimator, formula, data, panel = :panel, time = :time, kwargs...)
```
