```
stop_solver!(amp::AbstractManoptProblem, dss::DebugSolverState, i)
```

`stop_solver!`を拡張して、デバッグを実行するためのフックによってソルバーを停止するかどうかを判断します。これはデバッグリストの`:Stop`エントリに追加されました。
