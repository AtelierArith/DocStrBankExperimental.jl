```
device()::MTLDevice
```

Return the Metal GPU device associated with the current Julia task.

Since all M-series systems currently only externally show a single GPU, this function effectively returns the only system GPU.
