```
shfl_xor_sync(threadmask::UInt32, val, mask::Integer, width::Integer=32)
```

Shuffle a value from a lane based on bitwise XOR of own lane ID with `mask`, and synchronize threads according to `threadmask`.
