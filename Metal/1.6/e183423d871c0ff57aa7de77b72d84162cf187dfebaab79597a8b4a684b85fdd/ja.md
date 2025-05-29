```
simdgroup_store(src, dest::MtlDeviceArray{T}, matrix_origin=(1, 1))
```

8x8 SIMDグループ行列のデータをデバイスまたはスレッドグループメモリに格納します。 `T` は `Float16` または `Float32` のいずれかでなければなりません。

# 引数

  * `matrix_origin::NTuple{2, Int64}=(1, 1)`: 保存先のメモリにおける原点。
