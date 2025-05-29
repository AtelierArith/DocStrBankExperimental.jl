```
BufferedSaveCallback([backend], filename; [snapinterval = saveinterval], [flushinterval = 10snapinterval], [offset = 0.0], [dumprng = (s, sim) -> (s.nextsnap % 10 == 0)], [warn = IOWARN[]], [onconflict = ExportUtils.fail])
```

Create a [`SaveCallback`](@ref) that periodically saves simulation snapshots to `filename`.

Uses a [`PeriodicCallback`](@ref) with the given `interval` and `offset`.
