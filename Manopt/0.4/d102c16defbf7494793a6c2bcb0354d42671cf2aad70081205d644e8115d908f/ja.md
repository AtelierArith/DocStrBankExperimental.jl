```
step_solver!(amp::AbstractManoptProblem, dss::DebugSolverState, i)
```

ソルバーの `i` 番目のステップを拡張し、デバッグリストの `:BeforeIteration` および `:Iteration` エントリに追加されたデバッグプリントを実行するためのフックを追加します。
