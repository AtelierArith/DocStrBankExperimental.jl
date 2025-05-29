```
 convertToBasicSIAsExponents(abstractUnit::AbstractUnit)
```

Express a unit in terms of the seven basic SI units.

# Output

`(prefactor::Real, basicUnitAsExponents::BaseUnitExponents)`

The return variable `basicUnitAsExponents` indicates the powers of the seven basic SI units (kg, m, s, A, K, mol, cd) needed to represent the original unit. The return variable `prefactor` is the numerical prefactor relating the original unit to the returned unit.
