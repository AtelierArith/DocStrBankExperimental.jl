```
ThermalInsulator(material::String)
```

Outer constructor for `ThermalInsulator` types.  Material specified needs to have the following data in the database:

  * ρ (density): Density [kg/m³]
  * conductivity (thermal conductivity): a string with the thermal conductivity as a function of `T` [W/(m⋅K)]
