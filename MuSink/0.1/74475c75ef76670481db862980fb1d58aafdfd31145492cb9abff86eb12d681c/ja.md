```
step!(ws::Workspace, steps = 1; max_time = Inf, stepmode = ws.stepmode)
```

与えられた `stepmode` で `steps` Sinkhorn 更新ステップを実行します。

引数 `max_time` は、秒単位の時間制限を示し、その後はさらにステップが実行されません。
