```
openblas_getaffinity(; threadid, convert = true)
```

Query the affinity of the OpenBLAS thread with the given `threadid` (typically `1:BLAS.get_num_threads()`). By default, returns a vector respresenting the mask. If `convert=false` a `Ccpu_set_t` is returned instead.
