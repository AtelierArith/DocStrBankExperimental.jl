```
ReserveBattery{T} <: AbstractBattery{T}
```

A reserve battery storage, modelled as a `Storage` node. A battery storage nodes differs from a [`Battery`](@ref) node through allowing for the introduction of both upwards and downwards reserves.

!!! warning "Implementation details"
      * The discharge and charge capacities are independent of each other.
      * The values for the charge and discharge efficiencies must be smaller than 1.
      * The upwards and downwards reserves are implemented as resources leaving the battery. It is hence important to also provide a potential sink which determines the total reserve required in the system.


## Fields

  * **`id`** is the name/identifyer of the node.
  * **`charge::EMB.UnionCapacity`** are the charging parameters of the `BatteryStorage` node. Depending on the chosen type, the charge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`level::EMB.UnionCapacity`** are the level parameters of the `BatteryStorage` node. Depending on the chosen type, the charge parameters can include variable OPEX and/or fixed OPEX.
  * **`discharge::EMB.UnionCapacity`** are the discharging parameters of the `BatteryStorage` node. Depending on the chosen type, the discharge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`stor_res::ResourceCarrier`** is the stored `Resource`.
  * **`input::Dict{Resource, Real}`** are the input `Resource`s with corresponding efficiency value.
  * **`output::Dict{Resource, Real}`** are the output `Resource`s with corresponding efficiency value.
  * **`battery_life::AbstractBatteryLife`** is used for calculating the maximum battery lifetime and corresponding degradation of the Battery.
  * **`reserve_up::Vector{ResourceCarrier}`** are the `Resource`s used as reserve for providing energy to the system.
  * **`reserve_down::Vector{ResourceCarrier}`** are the `Resource`s used as reserve for removing energy from the system.
  * **`data::Vector{Data}`** additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
