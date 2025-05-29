```
openblas_setaffinity(mask; threadid)
```

Set the affinity of the OpenBLAS thread with the given `threadid` to the given `mask`.

The input `mask` should be one of the following:

  * a `BitArray` to indicate the mask directly
  * a vector of cpuids (in which case the mask will be constructed automatically)
