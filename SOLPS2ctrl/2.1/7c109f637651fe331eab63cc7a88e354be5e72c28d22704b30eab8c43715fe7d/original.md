```
gas_unit_converter(
    value_in::Float64,
    units_in::String,
    units_out::String;
    species::String="H",
    temperature::Float64=293.15,
)
```

Converts gas flows between different units. Uses ideal gas law to convert between Pressure * volume type flows / quantities and count / current types of units. There is a version that accepts floats in and outputs floats, and another that deals in Unitful quantities.
