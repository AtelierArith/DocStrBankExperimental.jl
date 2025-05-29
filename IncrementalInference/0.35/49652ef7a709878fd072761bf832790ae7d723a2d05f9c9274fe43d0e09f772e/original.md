```julia
cycleInitByVarOrder!(subfg, varorder; solveKey, logger)

```

Cycle through var order and initialize variables as possible in `subfg::AbstractDFG`. Return true if something was updated.

Notes:

  * assumed `subfg` is a subgraph containing only the factors that can be used.

      * including the required up or down messages
  * intended for both up and down initialization operations.

Dev Notes

  * Should monitor updates based on the number of inferred & solvable dimensions
