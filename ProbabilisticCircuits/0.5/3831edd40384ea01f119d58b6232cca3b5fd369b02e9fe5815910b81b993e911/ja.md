```
MAP(bpc::CuBitsProbCircuit, data::CuArray; batch_size, mars_mem=nothing)
```

与えられた回路とデータに対するMAP状態をGPU上で返します。欠損値は`missing`として示されるべきです。

MAP状態は、回路が分解可能かつ決定論的である場合にのみ正確であり、それ以外の場合は単なる近似です。

  * `bpc`: GPU上のBitCircuit
  * `data`: CuArray{Union{Missing, data_types...}}
  * `batch_size`
  * `mars_mem`: 必要ではなく、高度な使用法。メモリを再利用し、アロケーションを減らすためのCuMatrix。`prep_memory`および`cleanup_memory`を参照してください。
