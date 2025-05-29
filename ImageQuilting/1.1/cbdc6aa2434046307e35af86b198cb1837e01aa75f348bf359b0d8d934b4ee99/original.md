```
voxelreuse(trainimg::AbstractArray{T,N}, tilesize::Dims{N};
           overlap::NTuple{N,Float64}=ntuple(i->1/6,N),
           nreal::Integer=10, kwargs...)
```

Returns the mean voxel reuse in `[0,1]` and its standard deviation.

### Notes

  * The approximation gets better as `nreal` is made larger.
  * Keyword arguments `kwargs` are passed to `iqsim` directly.
