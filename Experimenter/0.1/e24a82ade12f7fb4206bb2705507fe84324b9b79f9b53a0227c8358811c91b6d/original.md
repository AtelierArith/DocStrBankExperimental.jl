```
@execute experiment database [mode=SerialMode use_progress=false directory=pwd()]
```

Runs the experiment out of global scope, saving results in the `database`, skipping all already executed trials.

# Args:

mode: Specifies SerialMode, MultithreadedMode or DistributedMode to execute serially or in parallel. use_progress: Shows a progress bar directory: Directory to change the current process (or worker processes) to for execution.
