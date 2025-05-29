```
SpecificH_Ps

Utility function that returns the speciic enthalpy [kJ/kg] from P [MPa]
and s [kJ/kgK].
The explicit backwards equations are only available in regions 1 and 2.
Input outside these will result in a DomainError exception.
If inputs have associated units, the value is returned with associated
units of kJ/kg via Uniful.jl.

Note: Do not use this function to attempt to find values on the saturation
line, as any rounding errors anywhere will result in a point on either side
of the phase boundary with large differences in enthalpy. Use SatHL/SatHV
for saturated phase enthalpies,
```
