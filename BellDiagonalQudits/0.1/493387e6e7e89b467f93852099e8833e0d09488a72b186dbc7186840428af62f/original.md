```
iterative_P1_P2_protocol(ρ, targetFid, n, d, stdBasis, maxIts)
```

Applies iterations of the P1_P2 routine to the `n`-copy input state `ρ` in `d` dimensions.  Iterates until `targetFid` or maximal number of iterations `maxIts` is reached.  Returns `distillable=true` if `targetFid` could be reached and fidelities and success probabilies with respect to the `stdbasis` for each iteration.
