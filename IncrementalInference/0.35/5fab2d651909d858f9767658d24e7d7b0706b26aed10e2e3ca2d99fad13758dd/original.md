```julia
getCliqDownMsgsAfterDownSolve(
    subdfg,
    cliq,
    solveKey;
    status,
    sender
)

```

Return dictionary of down messages consisting of all frontal and separator beliefs of this clique.

Notes:

  * Fetches numerical results from `subdfg` as dictated in `cliq`.
  * return LikelihoodMessage
