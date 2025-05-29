```
BufferedSaveCallback([backend], filename; [snapinterval = saveinterval], [flushinterval = 10snapinterval], [offset = 0.0], [dumprng = (s, sim) -> (s.nextsnap % 10 == 0)], [warn = IOWARN[]], [onconflict = ExportUtils.fail])
```

`filename`にシミュレーションスナップショットを定期的に保存する[`SaveCallback`](@ref)を作成します。

指定された`interval`と`offset`を使用して[`PeriodicCallback`](@ref)を使用します。
