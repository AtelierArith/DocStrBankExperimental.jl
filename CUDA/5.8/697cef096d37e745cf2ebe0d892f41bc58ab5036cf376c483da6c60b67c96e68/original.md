```
shfl_up_sync(threadmask::UInt32, val, delta::Integer, width::Integer=32)
```

Shuffle a value from a lane with lower ID relative to caller, and synchronize threads according to `threadmask`.
