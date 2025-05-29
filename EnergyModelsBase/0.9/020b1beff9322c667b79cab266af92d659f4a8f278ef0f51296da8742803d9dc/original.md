```
struct RefSink <: Sink
```

A reference [`Sink`](@ref) node. This node corresponds to a demand given by the field `cap`. The penalties introduced in the field `penalty` affect the variable OPEX for both a surplus and deficit.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the demand.
  * **`penalty::Dict{Symbol,<:TimeProfile}`** are penalties for surplus or deficits. The dictionary requires the  fields `:surplus` and `:deficit`.
  * **`input::Dict{<:Resource,<:Real}`** are the input [`Resource`](@ref)s with conversion value `Real`.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
