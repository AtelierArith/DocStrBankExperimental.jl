```
choose_batchsize(d, n; maxmemGB = 1.0, maxbatchsize = 2^14, sizeoneB = d*sizeof(Float64))
```

Computes the size (nb. of columns) of a batch, so that each column of the batch can be converted to a vector of size `sizeoneB` (in bytes) with a total memory constrained by `maxmemGB` (gigabytes).
