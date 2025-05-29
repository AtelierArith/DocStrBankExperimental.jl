```
GrB_finalize()
```

`GrB_finalize` must be called as the last GraphBLAS operation. `GrB_finalize` does not call `GrB_wait`; any pending computations are abandoned.
