```julia
addMsgFactors!(subfg, msg, dir; tags, attemptPriors)

```

Modify the `subfg::AbstractDFG` to include `msgs` as priors that are used during clique inference.

Notes

  * May be used initialization or inference, in both upward and downward directions.
  * `msgs` are identified by variable label `::Symbol`, and my consist of multiple beliefs.
  * Message sets from different cliques are identified by clique id `::Int`.
  * assume lower limit on number of particles is 5.
  * messages from children stored in vector or dict.

DevNotes

  * TODO Split dispatch on `dir`, rather than internal `if` statement.

Related

`deleteMsgFactors!`
