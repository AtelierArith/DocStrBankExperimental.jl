```
Battery{T} <: AbstractBattery{T}
```

A battery storage, modelled as a `Storage` node. A battery storage nodes differs from a [`RefStorage`](@extref EnergyModelsBase.RefStorage) node through:

1. incorporating a discharge capacity,
2. including charge and discharge efficiencies, and
3. allow for the introduction of battery degradation and lifetime reduction.

!!! warning "Implementation details"
      * The discharge and charge capacities are independent of each other.
      * The values for the charge and discharge efficiencies must be smaller than 1.


## Fields

  * **`id`** is the name/identifyer of the node.
  * **`charge::EMB.UnionCapacity`** are the charging parameters of the `BatteryStorage` node. Depending on the chosen type, the charge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`level::EMB.UnionCapacity`** are the level parameters of the `BatteryStorage` node. Depending on the chosen type, the charge parameters can include variable OPEX and/or fixed OPEX.
  * **`discharge::EMB.UnionCapacity`** are the discharging parameters of the `BatteryStorage` node. Depending on the chosen type, the discharge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`stor_res::ResourceCarrier`** is the stored `Resource`.
  * **`input::Dict{Resource, Real}`** are the input `Resource`s with corresponding efficiency value.
  * **`output::Dict{Resource, Real}`** are the output `Resource`s with corresponding efficiency value.
  * **`battery_life::AbstractBatteryLife`** is used for calculating the maximum battery lifetime and corresponding degradation of the Battery.
  * **`data::Vector{Data}`** additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
