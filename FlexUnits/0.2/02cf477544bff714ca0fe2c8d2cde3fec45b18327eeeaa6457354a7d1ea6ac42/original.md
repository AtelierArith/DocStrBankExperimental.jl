```
AffineUnits{D<:AbstractDimensions}(scale::Float64, offset::Float64, dims::D, symbol::Symbol)
```

Affine-dimensional unit (treated as a scalar when offset=0). Quantities with this unit are eagerly converted to dimmensional quantities for any operation, WHICH MAY BE UNITUITIVE because operations do not happen directly on values if there is an offset. If you want operations on the quantity  values directly, simply use "ustrip" and convert back.

julia> 1*(5u"°C") #Operations convert to Kelvin 278.15 K

julia> 1*(5u"°C") |> u"°C" #Converts operation results back to Celsius 5.0 °C

julia> (5u"°C" + 2u"°C") |> u"°C" #Operation adds values in Kelvin, results converted back to Celsius 280.15 °C

julia> (ustrip(5u"°C") + ustrip(2u"°C"))*u"°C" #Strips, adds raw quantity values, converts raw number to Celsius 7 °C
