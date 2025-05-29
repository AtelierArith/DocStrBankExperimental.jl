```
step!(ws::Workspace, steps = 1; max_time = Inf, stepmode = ws.stepmode)
```

Perform `steps` Sinkhorn update steps with a given `stepmode`.

The argument `max_time` denotes a time limit in seconds, after which no more steps are performed.
