```
loglikelihoods(bpc::CuBitsProbCircuit, data::CuArray; batch_size, mars_mem = nothing)
```

GPU上の各データポイントの対数尤度を返します。欠損値は `missing` で示されるべきです。

  * `bpc`: GPU上のBitCircuit
  * `data`: CuArray{Union{Missing, data_types...}}
  * `batch_size`
  * `mars_mem`: 必須ではなく、高度な使用法。メモリを再利用し、アロケーションを減らすためのCuMatrix。`prep_memory` と `cleanup_memory` を参照してください。
