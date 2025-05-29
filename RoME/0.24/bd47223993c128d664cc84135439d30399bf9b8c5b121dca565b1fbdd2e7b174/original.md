```julia
buildGraphChain!(; ...)
buildGraphChain!(fctData; ...)
buildGraphChain!(fctData, fctType; ...)
buildGraphChain!(
    fctData,
    fctType,
    preFct_args_cb;
    stopAfter,
    varType,
    solverParams,
    solvable,
    fctKwargs,
    varTags,
    fctTags,
    postpose_cb,
    doRef,
    dfg,
    inflation_fct,
    varRegex,
    varLast,
    varCount,
    varPrefix
)

```

Build a chain of variables with binary factors.

Notes:

  * `fctData[1]` aligns with the first variable (likely `:x0` for default empty `dfg`), and 

      * `:x0` has no previous variable/factor data.

DevNotes

  * TODO Consolidate with [`IIF._buildGraphByFactorAndTypes!`](@ref) and wrap in RoME?
