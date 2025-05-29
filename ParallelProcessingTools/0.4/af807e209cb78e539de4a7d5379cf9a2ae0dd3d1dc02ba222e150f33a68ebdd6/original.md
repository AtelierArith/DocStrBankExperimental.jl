```
worker_resources
```

Get the distributed Julia worker process resources currently available.

This may take some time as some code needs to be loaded on all processes. Automatically runs `ensure_procinit()` before querying worker resources.

Note: CPU ID information will only be available if [`ThreadPinning`](https://github.com/carstenbauer/ThreadPinning.jl) is loaded.
