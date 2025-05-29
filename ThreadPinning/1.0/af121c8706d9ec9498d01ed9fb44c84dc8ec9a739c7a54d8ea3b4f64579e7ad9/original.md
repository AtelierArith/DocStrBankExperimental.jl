```
openblas_unpinthread(; threadid)
```

Unpins the OpenBLAS thread with the given `threadid` by setting its affinity mask to all unity. Afterwards, the OS is free to move the OpenBLAS thread from one CPU thread to another.
