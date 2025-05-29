```
position(x::Union{AbstractGroup, AbstractIrrep})
```

If a position is associated with `x`, return it; if no position is associated, return `nothing`.

Applicable cases include `LittleGroup` (return the associated **k**-vector) and `SiteGroup` (returns the associated Wyckoff position), as well as their associated irrep types (`LGIrrep` and `SiteIrrep`).
