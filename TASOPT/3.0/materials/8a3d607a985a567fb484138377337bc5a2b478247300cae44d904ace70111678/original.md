```
StructuralAlloy(material::String; max_avg_stress = 1.1, safety_factor = 1.0)
```

Outer constructor for `StructuralAlloy` types.  Material specified needs to have the following data in the database:

  * ρ   : Density [kg/m³]
  * E   : Young's Modulus [Pa]
  * G   : Shear Modulus [Pa]
  * ν   : Poisson's Ratio [-]
  * σmax: Maximum Stress (Yield or Ultimate Strength) [Pa]
  * τmax: Maximum Shear [Pa]
