```julia
triggerSolve!(slam)

```

Trigger a factor graph `solveTree!(slam.dfg,...)` after clearing the solvable buffer `slam.??` (assuming the `manageSolveTree!` task is already running).

Notes

  * Used in combination with `manageSolveTree!`
