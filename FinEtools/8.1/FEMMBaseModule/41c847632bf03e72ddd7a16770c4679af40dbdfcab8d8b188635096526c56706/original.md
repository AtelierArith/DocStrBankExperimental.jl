```
field_elem_to_nodal!(
    self::AbstractFEMM,
    geom::NodalField{FT},
    ef::EFL,
    nf::NFL;
    kind = :weighted_average,
) where {FT, T<:Number, EFL<:ElementalField{T}, NFL<:NodalField{T}}
```

Make a nodal field  from an elemental field over the discrete manifold.

`ef` = ELEMENTAL field to supply the values `nf` = NODAL field to receive the values `kind` = default is `:weighted_average`; other options: `:max`

Returns `nf`.
