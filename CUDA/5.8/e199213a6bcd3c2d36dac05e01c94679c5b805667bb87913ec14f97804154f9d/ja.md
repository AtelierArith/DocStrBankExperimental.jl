```
shfl_sync(threadmask::UInt32, val, lane::Integer, width::Integer=32)
```

直接インデックスされたレーン `lane` から値をシャッフルし、`threadmask` に従ってスレッドを同期します。
