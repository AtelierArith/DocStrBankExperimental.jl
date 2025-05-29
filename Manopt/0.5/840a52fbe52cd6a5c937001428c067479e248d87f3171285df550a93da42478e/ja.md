```
initialize_solver!(ams::AbstractManoptProblem, rss::RecordSolverState)
```

ソルバーの初期化を拡張して、`:Start` エントリに追加されたレコードを実行するためのフックを追加します。
