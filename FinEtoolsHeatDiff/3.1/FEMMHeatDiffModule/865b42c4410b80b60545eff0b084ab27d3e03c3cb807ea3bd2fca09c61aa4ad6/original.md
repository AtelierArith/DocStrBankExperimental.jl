```
energy(self::FEMMHeatDiff, geom::NodalField{GFT},  temp::NodalField{FT}) where {GFT, FT}
```

Compute the "energy" integral over the interior domain.

The "energy" density is the dot product of the gradient of temperature and the heat flux.

# Arguments

  * `self` = model machine,
  * `geom` = geometry field,
  * `temp` = temperature field
