```
sync_warp(mask::Integer=FULL_MASK)
```

Waits threads in the warp, selected by means of the bitmask `mask`, have reached this point and all global and shared memory accesses made by these threads prior to `sync_warp()` are visible to those threads in the warp. The default value for `mask` selects all threads in the warp.

!!! note
    Requires CUDA >= 9.0 and sm_6.2

