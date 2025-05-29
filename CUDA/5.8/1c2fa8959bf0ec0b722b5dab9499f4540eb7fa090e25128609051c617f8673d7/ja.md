```
shfl_xor_sync(threadmask::UInt32, val, mask::Integer, width::Integer=32)
```

自分のレーンIDと`mask`のビット単位のXORに基づいてレーンから値をシャッフルし、`threadmask`に従ってスレッドを同期します。
