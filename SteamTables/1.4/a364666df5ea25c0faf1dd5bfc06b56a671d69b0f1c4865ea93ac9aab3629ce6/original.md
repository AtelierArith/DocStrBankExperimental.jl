```
SpecificU_Ps

Utility function that returns the internal energy [kJ/kgK] from P [MPa] and
s [kJ/kgK].
The explicit backwards equations are only available in regions 1 and 2.
Input outside these will result in a DomainError exception.
If inputs have associated units, the value is returned with associated
units of kJ/kg via Uniful.jl.
```
