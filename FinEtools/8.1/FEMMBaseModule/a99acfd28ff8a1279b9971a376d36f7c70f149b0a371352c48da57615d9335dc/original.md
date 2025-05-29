```
elemfieldfromintegpoints(
    self::FEMM,
    geom::NodalField{GFT},
    u::NodalField{UFT},
    dT::NodalField{TFT},
    quantity::Symbol,
    component::AbstractVector{IT};
    context...,
) where {FEMM<:AbstractFEMM, GFT<:Number, UFT<:Number, TFT<:Number, IT<:Integer}
```

Construct elemental field from integration points.

# Arguments

`geom`     - reference geometry field `u`        - displacement field `dT`       - temperature difference field `quantity`   - this is what you would assign to the 'quantity' argument            of the material update!() method. `component`- component of the 'quantity' array: see the material update()            method.

# Output

  * the new field that can be used to map values to colors and so on
