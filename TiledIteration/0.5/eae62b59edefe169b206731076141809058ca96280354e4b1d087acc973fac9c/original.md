```
padded_tilesize(T::Type, kernelsize::Dims, [ncache=2]) -> tilesize::Dims
```

Calculate a suitable tile size to approximately maximize the amount of productive work, given a stencil of size `kernelsize`. The element type of the array is `T`. Optionally specify `ncache`, the number of such arrays that you'd like to have fit simultaneously in L1 cache.

This favors making the first dimension larger, since the first dimension corresponds to individual cache lines.

# Examples

julia> padded_tilesize(UInt8, (3,3)) (768,18)

julia> padded_tilesize(UInt8, (3,3), 4) (512,12)

julia> padded_tilesize(Float64, (3,3)) (96,18)

julia> padded_tilesize(Float32, (3,3,3)) (64,6,6)
