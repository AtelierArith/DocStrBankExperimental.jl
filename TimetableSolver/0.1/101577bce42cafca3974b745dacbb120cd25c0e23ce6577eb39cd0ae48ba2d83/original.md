```
convertsolution(rawsolution::OrderedDict{Int,Int}, vardata::VariableData)::OrderedDict{String,String}
```

Return a solution in the form of a mapping from variable to its value (both as strings).

# Notes

  * Convert an `Int=>Int` solution to a `String=>String` one using the `inverse*` mappings defined in `vardata`.
