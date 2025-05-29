```
initialize_solver!(amp::AbstractManoptProblem, dss::DebugSolverState)
```

ソルバーの初期化を拡張して、デバッグリストの`:Start`エントリに追加された[`DebugAction`](@ref)を実行するフックを追加します。他のすべては（イテレーション番号`0`で）トリガーされ、可能なリセットを引き起こします。
