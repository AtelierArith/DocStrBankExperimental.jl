```
replace_variables!(model, throw = true, varname = vardef, varname2 = vardef2)
```

Replace one or more variables that already exists in the model (primary, secondary or parameters) with a new definition.

# Arguments

  * `model`: instance where variables is to be replaced
  * `varname=vardef::JutulVariables`: replace variable with `varname` by `vardef`
  * `throw=true`: throw an error if the named variable definition is not found in primary or secondary, otherwise silently return the `model`.
