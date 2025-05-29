```
SimpleHydrogenStorage{T} <: AbstractH2Storage{T}
```

`Storage` node in which the maximum discharge usage is directly linked to the charge capacity, that is it is not possbible to have a larger discharge usage than the charge capacity and a multiplier `discharge_charge`.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`charge::EMB.UnionCapacity`** are the charging parameters of the `SimpleHydrogenStorage` node. Depending on the chosen type, the charge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`level::EMB.UnionCapacity`** are the level parameters of the `SimpleHydrogenStorage` node. Depending on the chosen type, the charge parameters can include variable OPEX and/or fixed OPEX.
  * **`stor_res::Resource`** is the stored [`Resource`](@extref EnergyModelsBase.Resource).
  * **`input::Dict{<:Resource, <:Real}`** are the input [`Resource`](@extref EnergyModelsBase.Resource)s with conversion value `Real`.
  * **`output::Dict{<:Resource, <:Real}`** are the generated [`Resource`](@extref EnergyModelsBase.Resource)s with conversion value `Real`. Only relevant for linking and the stored [`Resource`](@extref EnergyModelsBase.Resource) as the output value is not utilized in the calculations.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
  * **`discharge_charge::Float64`** is the multiplier for specifying the maximum discharge rate relative to the charge rate. A value of `2.0` would imply that it is possible to have double the discharge rate compared to the installed charge capacity.
  * **`level_charge::Float64`** is the multiplier for specifying the installed storage level capacity relative to the installed storage charge capacity. It is used for checking input data in the case of a generic model and for limiting investments in the case of an [`AbstractInvestmentModel`](@extref EnergyModelsBase.AbstractInvestmentModel).
