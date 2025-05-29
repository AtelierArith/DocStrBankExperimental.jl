```
PumpedHydroStor{T} <: HydroStorage{T}
```

A pumped hydropower storage, modelled as a `Storage` node. A pumped hydro storage node allows for storing energy through pumping water into the reservoir. The current implementation is a simplified node in which no lower reservoir is required. Instead, it is assumed that the reservoir has an infinite size.

A pumped hydro storage node requires a capacity for both `charge` and `discharge` to account for the potential to store energy in the form of potential energy.

## Fields

  * **`id`** is the name/identifyer of the node.
  * **`charge::EMB.UnionCapacity`** are the charging parameters of the `PumpedHydroStor` node. Depending on the chosen type, the charge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`level::EMB.UnionCapacity`** are the level parameters of the `PumpedHydroStor` node. Depending on the chosen type, the charge parameters can include variable OPEX and/or fixed OPEX.
  * **`discharge::EMB.UnionCapacity`** are the discharging parameters of the `PumpedHydroStor` node. Depending on the chosen type, the discharge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`level_init::TimeProfile`** is the initial stored energy in the dam.
  * **`level_inflow::TimeProfile`** is the inflow of power per operational period.
  * **`level_min::TimeProfile`** is the minimum fraction of the reservoir capacity that has to remain in the `HydroStorage` node.
  * **`stor_res::ResourceCarrier`** is the stored `Resource`.
  * **`input::Dict{Resource, Real}`** are the input `Resource`s.
  * **`output::Dict{Resource, Real}`** can only contain one entry, the stored resource.
  * **`data::Vector{Data}`** additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
