```
converter = Converter(from_unit::Unit,to_unit::Unit)
```

Creates a converter function of numeric values in the `from_unit` to equivalent values in the `to_unit`.

```julia
using UDUnits
sys = System()
conv = Converter(sys["m/s"],sys["km/h"])
speed_in_m_per_s = 100.
speed_in_km_per_h = conv(speed_in_m_per_s)
```
