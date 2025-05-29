```
MultiStepSampler{names}(batchsize, n, stacksize, rng)
```

Sampler that fetches steps `[x, x+1, ..., x + n -1]` for each trace of each sampled index `x`. The samples are returned in an array of batchsize elements. For each element, n is truncated by the end of its episode. This means that the dimensions of each sample are not the same.
