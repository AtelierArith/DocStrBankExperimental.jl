```
shfl_sync(threadmask::UInt32, val, lane::Integer, width::Integer=32)
```

Shuffle a value from a directly indexed lane `lane`, and synchronize threads according to `threadmask`.
