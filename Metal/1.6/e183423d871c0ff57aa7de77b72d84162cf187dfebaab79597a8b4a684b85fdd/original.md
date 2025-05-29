```
simdgroup_store(src, dest::MtlDeviceArray{T}, matrix_origin=(1, 1))
```

Stores data from an 8x8 SIMD-group matrix into device or threadgroup memory. `T` must be either `Float16` or `Float32`.

# Arguments

  * `matrix_origin::NTuple{2, Int64}=(1, 1)`: origin in the destination memory to store to.
