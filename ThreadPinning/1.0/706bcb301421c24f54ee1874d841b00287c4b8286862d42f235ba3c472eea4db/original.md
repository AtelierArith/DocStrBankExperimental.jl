```
openblas_getcpuid(; threadid)
```

Get the id of the CPU thread on which the OpenBLAS thread with the given `threadid` is running on **according to its affinity**.

**Note:** If the OpenBLAS thread has not been pinned before, this function will error because the affinity mask highlights more than a single CPU thread by default.
