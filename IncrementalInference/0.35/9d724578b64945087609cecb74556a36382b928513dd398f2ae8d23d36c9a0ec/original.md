```julia
getFactorsAmongVariablesOnly(dfg, varlist; unused)

```

Return list of factors which depend only on variables in variable list in factor graph – i.e. among variables.

## Notes

  * `unused::Bool=true` will disregard factors already used – i.e. disregard where `potentialused=true`
