```
simdgroup_load(data::MtlDeviceArray{T}, matrix_origin=(1, 1))
```

デバイスまたはスレッドグループメモリから8x8 SIMDグループ行列にデータをロードし、それを返します。 `T` は `Float16` または `Float32` のいずれかでなければなりません。

# 引数

  * `matrix_origin::NTuple{2, Int64}=(1, 1)`: ロード元のソースメモリにおける起点。
