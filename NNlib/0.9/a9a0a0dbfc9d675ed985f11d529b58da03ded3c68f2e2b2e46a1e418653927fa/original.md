```
upsample_trilinear(x::AbstractArray{T,5}, scale::NTuple{3,Real}; align_corners::Bool = true)
upsample_trilinear(x::AbstractArray{T,5}; size::NTuple{3,Integer}, align_corners::Bool = true)
```

Upsamples the first 3 dimensions of the array `x` by the upsample factors stored in `scale`, using trilinear interpolation. As an alternative to using `scale`, the resulting image `size` can be directly specified with a keyword argument.

The size of the output is equal to `(scale[1]*S1, scale[2]*S2, scale[3]*S3, S4, S5)`, where `S1, S2, S3, S4, S5 = size(x)`.

# Examples

```julia
upsample_trilinear(x, (2, 3, 4))
upsample_trilinear(x; size=(4, 9, 11))  # specify ouput size instead
upsample_trilinear(x, (2.5, 3.5, pi))  # non-integer scaling factors are allowed
```
