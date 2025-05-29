```
requiresWritingCheckpoint()::Bool
```

Check if the solver has to write a checkpoint. preCICE refuses to proceed if writing a checkpoint is required, but this method isn't called prior to advance().
