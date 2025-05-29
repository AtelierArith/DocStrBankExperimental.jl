```
upsample_linear(x::AbstractArray{T,3}, scale::Real; align_corners::Bool = true)
upsample_linear(x::AbstractArray{T,3}; size::Integer, align_corners::Bool = true)
```

Upsamples the first dimension of the array `x` by the upsample provided `scale`, using linear interpolation. As an alternative to using `scale`, the resulting array `size` can be directly specified with a keyword argument.

The size of the output is equal to `(scale*S1, S2, S3)`, where `S1, S2, S3 = size(x)`.
