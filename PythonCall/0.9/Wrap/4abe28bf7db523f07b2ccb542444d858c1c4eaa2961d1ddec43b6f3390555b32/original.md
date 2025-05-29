```
PyArray{T,N,M,L,R}(x; copy=true, array=true, buffer=true)
```

Wrap the Python array `x` as a Julia `AbstractArray{T,N}`.

The input `x` can be `bytes`, `bytearray`, `array.array`, `numpy.ndarray` or anything satisfying the buffer protocol (if `buffer=true`) or the numpy array interface (if `array=true`).

If `copy=false` then the resulting array is guaranteed to directly wrap the data in `x`. If `copy=true` then a copy is taken if necessary to produce an array.

The type parameters are all optional, and are:

  * `T`: The element type.
  * `N`: The number of dimensions.
  * `M`: True if the array is mutable.
  * `L`: True if the array supports fast linear indexing.
  * `R`: The element type of the underlying buffer. Often equal to `T`.
