```
requiresReadingCheckpoint()::Bool
```

Check if the solver has to read an iteration checkpoint. preCICE refuses to proceed if reading a checkpoint is required, but this method isn't called prior to advance().
