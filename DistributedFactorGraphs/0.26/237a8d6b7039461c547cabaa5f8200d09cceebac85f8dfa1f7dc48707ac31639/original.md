```julia
findVariableNearTimestamp(dfg, timest; ...)
findVariableNearTimestamp(
    dfg,
    timest,
    regexFilter;
    tags,
    solvable,
    warnDuplicate,
    number
)

```

Find and return nearest variable labels per delta time.  Function will filter on `regexFilter`, `tags`, and `solvable`.

Notes

  * Returns `Vector{Tuple{Vector{Symbol}, Millisecond}}`

DevNotes:

  * TODO `number` should allow returning more than one for k-nearest matches.
  * Future versions likely will require some optimization around the internal `getVariable` call.

      * Perhaps a dedicated/efficient `getVariableTimestamp` for all DFG flavors.

Related

ls, listVariables, findClosestTimestamp
