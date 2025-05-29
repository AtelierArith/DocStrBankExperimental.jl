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

式の構文は次のとおりです：

```
@formula(response ~ exogenous + (endogenous ~ instruments) + absorb(highdimscontrols))
```

データはTables.jl APIを実装し、CategoricalArrays (CategoricalVector) を使用する必要があります。

重みは `StatsBase.FrequencyWeights` として取得されます。

パネルおよび時間指標は縦断的推定器に使用されます。

# 例

```
model = fit(EconometricModel, formula, data, kwargs...)
model = fit(BetweenEstimator, formula, data, panel = :panel, kwargs...)
model = fit(RandomEffectsEstimator, formula, data, panel = :panel, time = :time, kwargs...)
```
