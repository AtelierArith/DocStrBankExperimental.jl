```
fieldfromintegpoints(
    self::FEMM,
    geom::NodalField{GFT},
    u::NodalField{UFT},
    dT::NodalField{TFT},
    quantity::Symbol,
    component::AbstractVector{IT};
    context...,
) where {FEMM<:AbstractFEMM, GFT<:Number, UFT<:Number, TFT<:Number, IT<:Integer}
```

Construct nodal field from integration points.

# Arguments

  * `geom`     - reference geometry field
  * `u`        - displacement field
  * `dT`       - temperature difference field
  * `quantity`   - this is what you would assign to the 'quantity' argument          of the material update!() method.
  * `component`- component of the 'quantity' array: see the material update()          method.

Keyword arguments

  * `nodevalmethod` = `:invdistance` (the default) or `:averaging`;
  * `reportat` = at which point should the  element quantities be reported?   This argument is interpreted inside the `inspectintegpoints()` method.

# Output

  * the new field that can be used to map values to colors and so on
