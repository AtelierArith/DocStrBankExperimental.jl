```
loglikelihoods(bpc::CuBitsProbCircuit, data::CuArray; batch_size, mars_mem = nothing)
```

Returns loglikelihoods for each datapoint on gpu. Missing values should be denoted by `missing`.

  * `bpc`: BitCircuit on gpu
  * `data`: CuArray{Union{Missing, data_types...}}
  * `batch_size`
  * `mars_mem`: Not required, advanced usage. CuMatrix to reuse memory and reduce allocations. See `prep_memory` and `cleanup_memory`.
