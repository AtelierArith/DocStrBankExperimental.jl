```julia
manageSolveTree!(dfg, mss; dbg, timinglog, limitfixeddown)

```

Asynchronous solver manager that can run concurrently while other Tasks are modifying a common distributed factor graph object.

Notes

  * When adding Variables and Factors, use `solvable=0` to disable the new fragments until ready for inference.

      * e.g. `addVariable!(fg, :x45, Pose2, solvable=0)`
      * These parts of the factor graph can simply be activated for solving `setSolvable!(fg, :x45, 1)`
