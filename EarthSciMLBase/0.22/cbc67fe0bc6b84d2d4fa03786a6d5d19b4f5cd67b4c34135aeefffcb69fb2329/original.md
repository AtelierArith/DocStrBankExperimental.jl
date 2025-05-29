```julia
ConstantWind(t, vals; name)

```

Construct a constant wind velocity model component with the given wind speed(s), which should include units. For example, `ConstantWind(t, 1u"m/s", 2u"m/s")`.
