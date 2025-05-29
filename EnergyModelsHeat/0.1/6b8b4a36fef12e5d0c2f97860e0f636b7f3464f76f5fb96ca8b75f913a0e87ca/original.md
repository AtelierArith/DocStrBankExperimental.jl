```
ThermalEnergyStorage{T} <: Storage{T}
```

A `ThermalEnergyStorage` that functions mostly like a [`RefStorage`](@extref EnergyModelsBase.RefStorage) with the additional option to include thermal energy losses. Heat losses are quantified through a heat loss factor that describes the amount of thermal energy that is lost in relation to the storage level from the previous timeperiod.

The main difference to [`RefStorage`](@extref EnergyModelsBase.RefStorage) is that these heat losses do not occur while charging or discharging, *i.e.*, they are proportional to the storage level.

!!! warning "StorageBehavior"
    `ThermalEnergyStorage` in its current implementation only supports [`CyclicRepresentative`](@extref EnergyModelsBase.CyclicRepresentative) as storage behavior. This input is not a required input due to the utilization of an inner constructor.


# Fields

  * **`id`** is the name/identifier of the node.
  * **`charge::AbstractStorageParameters`** are the charging parameters of the `ThermalEnergyStorage` node. Depending on the chosen type, the charge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`level::AbstractStorageParameters`** are the level parameters of the `ThermalEnergyStorage`. Depending on the chosen type, the charge parameters can include variable OPEX and/or fixed OPEX.
  * **`stor_res::Resource`** is the stored [`Resource`](@extref EnergyModelsBase.Resource).
  * **`heat_loss_factor::Float64`** are the relative heat losses in percent.
  * **`input::Dict{<:Resource,<:Real}`** are the input [`Resource`](@extref EnergyModelsBase.Resource)s with conversion value `Real`.
  * **`output::Dict{<:Resource,<:Real}`** are the generated [`Resource`](@extref EnergyModelsBase.Resource)s with conversion value `Real`. Only relevant for linking and the stored [`Resource`](@extref EnergyModelsBase.Resource) as the output value is not utilized in the calculations.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
