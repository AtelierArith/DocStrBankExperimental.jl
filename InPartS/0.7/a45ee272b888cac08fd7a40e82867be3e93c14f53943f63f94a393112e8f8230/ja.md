```
SaveCallback([backend], filename; [interval = 1.0], [offset = 0.0], [dumprng = (s, sim) -> (s.nextsnap % 10 == 0)], [warn = IOWARN[]], [onconflict = ExportUtils.fail])
```

[`SaveCallback`](@ref) を作成して、定期的にシミュレーションのスナップショットを `filename` に保存します。

指定された `interval` と `offset` を使用して [`PeriodicCallback`](@ref) を使用します。
