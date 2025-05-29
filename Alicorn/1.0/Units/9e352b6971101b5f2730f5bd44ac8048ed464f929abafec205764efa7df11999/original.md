```
convertToBasicSI(abstractUnit::AbstractUnit)
```

Express a unit in terms of the seven basic SI units.

# Output

`(prefactor::Real, basicUnit::Unit)`

The return variable `basicUnit` only contains powers of the seven basic SI units (kg, m, s, A, K, mol, cd). The return variable `prefactor` is the numerical prefactor relating the original unit to the returned unit.
