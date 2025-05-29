```
CO2Storage{T} <: Storage{T}
```

This node has an installed injection rate capacity through `charge` and a storage capacity `level`.

The storage level (accountet by the optimization variable `stor_level`) will increase during all strategic periods (sp), *i.e.*, the stored resource can not be taken out of the storage.

The initial storage level in a strategic period is set to the storage level at the end of the prevoious sp. Note that the increased storage level during a sp is multiplied with the length of the sp when the initial storage level for the next sp is set.

This is achieved through the parametric input [`AccumulatingStrategic`](@ref). This input is not a required input due to the utilization of an inner constructor.

# Fields

  * **`id`** is the name/identifyer of the node.
  * **`charge::EMB.UnionCapacity`** are the charging parameters of the `CO2Storage` node. Depending on the chosen type, the charge parameters can include variable OPEX and/or fixed OPEX.
  * **`level::EMB.UnionCapacity`** are the level parameters of the `CO2Storage` node. Depending on the chosen type, the charge parameters can include variable OPEX and/or fixed OPEX.
  * **`stor_res::Resource`** is the stored `Resource`.
  * **`input::Dict{<:Resource, <:Real}`** are the input `Resource`s with conversion value `Real`.
  * **`data::Array{<:Data}`** is the additional data (e.g. for investments). The field `data` is conditional through usage of a constructor.
