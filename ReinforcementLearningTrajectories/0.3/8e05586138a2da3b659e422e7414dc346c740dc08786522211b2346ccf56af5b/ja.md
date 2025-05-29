```
BatchSampler{names}(;batchsize, rng=Random.GLOBAL_RNG)
BatchSampler{names}(batchsize ;rng=Random.GLOBAL_RNG)
```

指定された `names` の各トレースに対して、`batchsize` の例の **ONE** バッチを均等にサンプリングします。`names` が設定されていない場合、すべてのトレースがサンプリングされます。
