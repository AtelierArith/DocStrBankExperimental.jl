```
@with_kw mutable struct Section
```

Represents a wing section with leading edge, trailing edge, and aerodynamic properties.

# Fields

  * `LE_point::MVec3` = zeros(MVec3): Leading edge point coordinates
  * `TE_point::MVec3` = zeros(MVec3): Trailing edge point coordinates
  * `aero_model`::AeroModel = INVISCID: [AeroModel](@ref)
  * `aero_data`::AeroData = nothing: See: [AeroData](@ref)
