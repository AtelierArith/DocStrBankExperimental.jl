```
HydroStor{T} <: HydroStorage{T}
```

A regulated hydropower storage, modelled as a `Storage` node. A regulated hydro storage node requires a capacity for the `discharge` and does not have a required inflow from the model, except for water inflow from outside the model, although it requires a field `input`.

## Fields

  * **`id`** is the name/identifyer of the node.
  * **`level::EMB.UnionCapacity`** are the level parameters of the `HydroStor` node. Depending on the chosen type, the charge parameters can include variable OPEX and/or fixed OPEX.
  * **`discharge::EMB.UnionCapacity`** are the discharging parameters of the `HydroStor` node. Depending on the chosen type, the discharge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`level_init::TimeProfile`** is the initial stored energy in the dam.
  * **`level_inflow::TimeProfile`** is the inflow of power per operational period.
  * **`level_min::TimeProfile`** is the minimum fraction of the reservoir capacity that has to remain in the `HydroStorage` node.
  * **`stor_res::ResourceCarrier`** is the stored `Resource`.
  * **`input::Dict{Resource, Real}`** are the input `Resource`s. In the case of a `HydroStor`, this field can be left out.
  * **`output::Dict{Resource, Real}`** can only contain one entry, the stored resource.
  * **`data::Vector{Data}`** additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
