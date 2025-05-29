```julia
buildCliqSubgraph(dfg, cliq; ...)
buildCliqSubgraph(dfg, cliq, subfg; solvable, verbose)

```

Build a new subgraph from `fgl<:AbstractDFG` containing all variables and factors associated with `cliq`.  Additionally add the upward message prior factors as needed for belief propagation (inference).

Notes

  * `cliqsym::Symbol` defines the cliq where variable appears as a frontal variable.
  * `varsym::Symbol` defaults to the cliq frontal variable definition but can in case a separator variable is required instead.

DevNotes

  * TODO review, are all updates atomic?? Then perhaps in-memory only can be reduced to references back to csmc.dfg.
