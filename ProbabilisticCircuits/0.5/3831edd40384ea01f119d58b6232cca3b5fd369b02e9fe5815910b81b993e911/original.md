```
MAP(bpc::CuBitsProbCircuit, data::CuArray; batch_size, mars_mem=nothing)
```

Retruns the MAP states for a given circuit and data on gpu. Missing values should be denoted as `missing`.

Note that the MAP states are exact only when the circuit is both decomposable and deterministic, otherwise its just an approximation.

  * `bpc`: BitCircuit on gpu
  * `data`: CuArray{Union{Missing, data_types...}}
  * `batch_size`
  * `mars_mem`: Not required, advanced usage. CuMatrix to reuse memory and reduce allocations. See `prep_memory` and `cleanup_memory`.
