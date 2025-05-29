```
field_nodal_to_elem!(
    self::AbstractFEMM,
    geom::NodalField{FT},
    nf::NFL,
    ef::EFL;
    kind = :weighted_average,
) where {FT<:Number, T, EFL<:ElementalField{T}, NFL<:NodalField{T}}
```

Make an elemental field  from a nodal field over the discrete manifold.

`nf` = NODAL field to supply the values `ef` = ELEMENTAL field to receive the values `kind` = default is `:weighted_average`; other options: `:max`

Returns `ef`.
