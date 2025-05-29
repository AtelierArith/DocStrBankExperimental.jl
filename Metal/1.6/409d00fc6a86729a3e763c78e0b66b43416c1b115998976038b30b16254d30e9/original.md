```
simdgroup_load(data::MtlDeviceArray{T}, matrix_origin=(1, 1))
```

Loads data from device or threadgroup memory into an 8x8 SIMD-group matrix and returns it. `T` must be either `Float16` or `Float32`.

# Arguments

  * `matrix_origin::NTuple{2, Int64}=(1, 1)`: origin in the source memory to load from.
