```
shfl_down_sync(threadmask::UInt32, val, delta::Integer, width::Integer=32)
```

呼び出し元に対してIDが高いレーンから値をシャッフルし、`threadmask`に従ってスレッドを同期します。
