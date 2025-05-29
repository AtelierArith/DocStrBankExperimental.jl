```julia
addDownVariableFactors!(dfg, subfg, cliq; ...)
addDownVariableFactors!(dfg, subfg, cliq, logger; solvable)

```

Special function to add a few variables and factors to the clique sub graph required for downward solve in CSM.

Dev Notes

  * There is still some disparity on whether up and down solves of tree should use exactly the same subgraph...  'between for up and frontal connected for down'
