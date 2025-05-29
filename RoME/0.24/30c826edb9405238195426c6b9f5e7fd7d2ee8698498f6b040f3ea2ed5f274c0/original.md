```julia
enableSolveAllNotDRT!(dfg; solvable)

```

Remove all marginalization and make solvable (=1) all variables and factors that don't contain `drt` in their label.

Notes

  * Dead Reckon Tether (DRT)

DevNotes

  * Legacy, poor implementation, needs to be improved

Related

dontMarginalizeVariablesAll!, setSolvable!, defaultFixedLagOnTree!
