```julia
checkSolveStrideTrigger!(slam; force)

```

Check and trigger a solve if `slam.poseCount` reached the solve stride `slam.solveSettings.solveStride`.

Notes

  * Used in combination with `manageSolveTree!`

Related

triggerSolve!
