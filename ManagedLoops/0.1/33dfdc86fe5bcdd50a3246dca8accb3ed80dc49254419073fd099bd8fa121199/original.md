```
mgr_nosimd = no_simd(mgr::LoopManager)
```

Returns a manager similar to `mgr` but with SIMD disabled.

!!! tip
    Due to implementation details, not all loops support SIMD. If errors are thrown when offloading a loop on an SIMD-enabled manager, use this function.

