```
mutable struct Stage{L <: LifeStage}
    μ_temperature_response::TemperatureResponse
    q_temperature_response::TemperatureResponse
    n::Union{Nothing, Int64}
    density::Density{<: DensityDependence}
    dependency::Union{Nothing, Type{<:LifeStage}}
    N0::Int64
end
```

Data for life stages. Applies to any organism represented by stage-structured population equations.

# Arguments

  * `μ_temperature_response::TemperatureResponse`: Mortality rate. Responsive to temperature.
  * `q_temperature_response::TemperatureResponse`: Developmental rate. 1/total time (days or portion thereof) spent in stage. Responsive to temperature.
  * `n::Union{Nothing, Int64}`: Number of bins allocated to stage (parameter, Erlang distribution).
  * `density::Density`: Specify density dependence model.
  * `dependency::Union{Nothing, Type{<:LifeStage}}`: Organism internal reference, do not modify.
  * `N0::Int64`: Initial stage-specific population count per node. Specify "0" for all stages except `Female` life stage.
