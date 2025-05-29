```
SizedArray{Tuple{dims...}}(array)
```

Wraps an `AbstractArray` with a static size, so to take advantage of the (faster) methods defined by StaticArrays.jl. The size is checked once upon construction to determine if the number of elements (`length`) match, but the array may be reshaped.

The aliases `SizedVector{N}` and `SizedMatrix{N,M}` are provided as more convenient names for one and two dimensional `SizedArray`s. For example, to wrap a 2x3 array `a` in a `SizedArray`, use `SizedMatrix{2,3}(a)`.
