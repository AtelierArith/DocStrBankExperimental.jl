```julia
checkSolveStrideTrigger!(slam; force)

```

`slam.poseCount` が解のストライド `slam.solveSettings.solveStride` に達した場合に、解をチェックしてトリガーします。

ノート

  * `manageSolveTree!` と組み合わせて使用されます。

関連

triggerSolve!
