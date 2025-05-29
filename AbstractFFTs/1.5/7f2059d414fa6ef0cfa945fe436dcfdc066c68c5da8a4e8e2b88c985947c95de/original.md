```
irfft(A, d [, dims])
```

Inverse of [`rfft`](@ref): for a complex array `A`, gives the corresponding real array whose FFT yields `A` in the first half. As for [`rfft`](@ref), `dims` is an optional subset of dimensions to transform, defaulting to `1:ndims(A)`.

`d` is the length of the transformed real array along the `dims[1]` dimension, which must satisfy `div(d,2)+1 == size(A,dims[1])`. (This parameter cannot be inferred from `size(A)` since both `2*size(A,dims[1])-2` as well as `2*size(A,dims[1])-1` are valid sizes for the transformed real array.)
