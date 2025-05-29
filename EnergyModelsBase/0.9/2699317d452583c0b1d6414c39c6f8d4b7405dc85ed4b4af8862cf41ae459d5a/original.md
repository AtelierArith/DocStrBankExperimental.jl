```
struct RefStorage{T} <: Storage{T}
```

A reference [`Storage`](@ref) node.

This node is designed to store either a [`ResourceCarrier`](@ref) or a [`ResourceEmit`](@ref). It is designed as a parametric type through the type parameter `T` to differentiate between different cyclic behaviours. Note that the parameter `T` is only used for dispatching, but does not carry any other information. Hence, it is simple to fast switch between different [`StorageBehavior`](@ref)s.

The current implemented cyclic behaviours are [`CyclicRepresentative`](@ref), [`CyclicStrategic`](@ref), and [`AccumulatingEmissions`](@ref).

# Fields

  * **`id`** is the name/identifier of the node.
  * **`charge::AbstractStorageParameters`** are the charging parameters of the [`Storage`](@ref) node. Depending on the chosen type, the charge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`level::AbstractStorageParameters`** are the level parameters of the [`Storage`](@ref) node. Depending on the chosen type, the charge parameters can include variable OPEX and/or fixed OPEX.
  * **`stor_res::Resource`** is the stored [`Resource`](@ref).
  * **`input::Dict{<:Resource,<:Real}`** are the input [`Resource`](@ref)s with conversion value `Real`.
  * **`output::Dict{<:Resource,<:Real}`** are the generated [`Resource`](@ref)s with conversion value `Real`. Only relevant for linking and the stored [`Resource`](@ref) as the output value is not utilized in the calculations.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
