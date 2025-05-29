```
step_solver!(amp::AbstractManoptProblem, rss::RecordSolverState, i)
```

ソルバーの `i` 番目のステップを拡張し、`:Iteration` エントリに追加されたレコードを実行するためのフックを追加します。
