```
BatchSampler{names}(;batchsize, rng=Random.GLOBAL_RNG)
BatchSampler{names}(batchsize ;rng=Random.GLOBAL_RNG)
```

Uniformly sample **ONE** batch of `batchsize` examples for each trace specified in `names`. If `names` is not set, all the traces will be sampled.
