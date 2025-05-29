```
TBLogger(logdir[, tb_increment]; 
        time=time(), 
        prefix="",
        purge_step=nothing, 
        step_increment=1, 
        min_level=Logging.Info)
```

Creates a TensorBoardLogger in the folder `logdir`. The second (optional) argument specifies the behaviour if the `logdir` already exhists: the default choice `tb_increment` appends an increasing number 1,2... to `logdir`. Other choices are `tb_overwrite`, which overwrites the previous folder, and `tb_append`, which adds to any existing logs.

Optional keyword argument `prefix` can be passed to prepend a path to the file name (note, not the log directory). See `create_eventfile()`

If a `purge_step::Int` is passed, every step before `purge_step` will be ignored by tensorboard (usefull in the case of restarting a crashed computation).

`min_level` specifies the minimum level of messages logged to tensorboard.
