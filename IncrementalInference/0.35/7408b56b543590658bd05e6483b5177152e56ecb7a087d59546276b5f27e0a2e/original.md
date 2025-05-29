```julia
getCliqVarIdsPriors(cliq)
getCliqVarIdsPriors(cliq, allids)
getCliqVarIdsPriors(cliq, allids, partials)

```

Get variable ids`::Int` with prior factors associated with this `cliq`.

Notes:

  * does not include any singleton messages from upward or downward message passing.
