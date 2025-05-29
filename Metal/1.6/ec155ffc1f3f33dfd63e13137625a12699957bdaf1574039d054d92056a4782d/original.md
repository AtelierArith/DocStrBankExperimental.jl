```
simd_shuffle_down(data::T, delta::Integer)
```

Return `data` from the thread whose SIMD lane ID is the sum of caller's SIMD lane ID and `delta`.

The value for `delta` must be the same for all threads in the SIMD-group. This function doesn't modify the upper `delta` lanes of `data` because it doesn't wrap values around the SIMD-group.

T must be one of the following: Float32, Float16, Int32, UInt32, Int16, UInt16, Int8, or UInt8
