```
GrB_init(mode)
```

`GrB_init` must called before any other GraphBLAS operation. `GrB_init` defines the mode that GraphBLAS will use: blocking or non-blocking. With blocking mode, all operations finish before returning to the user application. With non-blocking mode, operations can be left pending, and are computed only when needed.
