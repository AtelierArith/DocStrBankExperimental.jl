```
HydroReservoir{T} <: EMB.Storage{T}
```

A regulated hydropower reservoir, modelled as a `Storage` node.

A `HydroReservoir` differs from [`HydroStor`](@ref) and[`PumpedHydroStor`](@ref) nodes as it models the stored energy in the form of water through the potential energy. It can only be used in conjunction with [`HydroGenerator`](@ref) nodes.

## Fields

  * **`id`** is the name/identifyer of the node.
  * **`vol::EMB.UnionCapacity`** are the storage volume parameters of the `HydroReservoir` node (typically million cubic meters).
  * **`vol_inflow::TimeProfile`** is the water inflow to the reservoir (typically million cubic per time unit).
  * **`stor_res::ResourceCarrier`** is the stored `Resource`.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments or constraints through [`AbstractScheduleType`](@ref)). The field `data` is conditional through usage of a constructor.
