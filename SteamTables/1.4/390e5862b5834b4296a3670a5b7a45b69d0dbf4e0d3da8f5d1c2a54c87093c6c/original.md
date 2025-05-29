```
SpecificH

Utility function that returns the specific enthalpy [kJ/kg] from P [MPa]
and T [K].
If inputs have associated units, the value is returned with associated
units of kJ/kg via Uniful.jl.

Note: Do not use this function to attempt to find values on the saturation
line, as any rounding errors anywhere will result in a point on either side
of the phase boundary with large differences in enthalpy. Use SatHL/SatHV
for saturated phase enthalpies.
```
