```
struct RefSource <: Source
```

A reference [`Source`](@ref) node. The reference [`Source`](@ref) node allows for a time varying capacity which is normalized to a conversion value of 1 in the field `input`. Note, that if you include investments, you can only use as `TimeProfile` a `FixedProfile` or `StrategicProfile`.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed capacity.
  * **`opex_var::TimeProfile`** is the variable operating expense per per capacity usage through the variable `:cap_use`.
  * **`opex_fixed::TimeProfile`** is the fixed operating expense per installed capacity through the variable `:cap_inst`.
  * **`output::Dict{<:Resource,<:Real}`** are the generated [`Resource`](@ref)s with conversion value `Real`.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
