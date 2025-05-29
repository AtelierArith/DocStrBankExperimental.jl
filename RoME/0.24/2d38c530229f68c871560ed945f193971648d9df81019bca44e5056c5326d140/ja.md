```julia
triggerSolve!(slam)

```

ファクターグラフ `solveTree!(slam.dfg,...)` をトリガーし、解決可能なバッファ `slam.??` をクリアした後に実行します（`manageSolveTree!` タスクがすでに実行中であると仮定します）。

ノート

  * `manageSolveTree!` と組み合わせて使用されます。
