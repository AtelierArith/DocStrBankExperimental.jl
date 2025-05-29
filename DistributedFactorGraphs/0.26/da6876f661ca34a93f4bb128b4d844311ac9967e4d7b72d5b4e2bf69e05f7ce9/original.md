```julia
updateVariableSolverData!(dfg, variablekey, vnd; ...)
updateVariableSolverData!(
    dfg,
    variablekey,
    vnd,
    useCopy;
    ...
)
updateVariableSolverData!(
    dfg,
    variablekey,
    vnd,
    useCopy,
    fields;
    warn_if_absent
)

```

Update variable solver data if it exists, otherwise add it.

Notes:

  * `useCopy=true` to copy solver data and keep separate memory.
  * Use `fields` to updated only a few VND.fields while adhering to `useCopy`.

Related

mergeVariableSolverData!
