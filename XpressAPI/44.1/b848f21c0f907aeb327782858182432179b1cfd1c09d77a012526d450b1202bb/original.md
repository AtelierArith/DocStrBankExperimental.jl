```
XPRS_IISOPS
```

Selects which part of the restrictions (bounds, constraints, entities) should always be kept in an IIS. (integer)

This is useful if certain types of restrictions cannot be violated, thus they are known not to be the cause of infeasibility. The IIS obtained this way is irreducible only for the non-protected restrictions. This control has an effect only on the deletion filter of the IIS procedure.

Default value: `0`, all restrictions are valid candidates for removal

Values are a bitset: bit 0 : Keep binary integralities. bit 1 : Keep the 0 lower bounds of variables. bit 2 : Keep fixed variables. bit 3 : Keep all variable bounds. bit 4 : Keep all general integer entities, except binaries. bit 5 : Keep all equality constraints. bit 6 : Keep all general constraints. bit 7 : Keep all piecewise linear constraints. bit 8 : Keep all specially ordered set (SOS) constraints. bit 9 : Keep all indicator constraints. bit 10 : Keep all delayed rows. bit 11 : Keep all constraints.
