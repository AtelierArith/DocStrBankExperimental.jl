```
absoluteunit(::Units)
absoluteunit(::Quantity)
```

Given a unit or quantity, which may or may not be affine (e.g. `°C`), return the corresponding unit on the absolute temperature scale (e.g. `K`). Passing a [`Unitful.ContextUnits`](@ref) object will return another `ContextUnits` object with the same promotion unit, which may be an affine unit, so take care.
