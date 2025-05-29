```
ResizableArray{T}(undef, dims...)
```

yields a resizable array with un-initialized elements of type `T` and dimensions `dims...`. Dimensions may be a tuple of integers or a a list of integers. The number `N` of dimensions may be explicitly specified:

```
ResizableArray{T,N}(undef, dims...)
```

To create an empty resizable array of given rank and element type, call:

```
ResizableArray{T,N}()
```

The dimensions of a resizable array `A` may be changed by calling `resize!(A,dims)` with `dims` the new dimensions. The number of dimensions must remain unchanged but the length of the array may change. Depending on the type of the object backing the storage of the array, it may be possible or not to augment the number of elements of the array. When array elements are stored in a regular Julia vector, the number of element can always be augmented. Changing only the last dimension of a resizable array preserves its contents.

Resizable arrays are designed to re-use storage if possible to avoid calling the garbage collector. This may be useful for real-time applications. As a consequence, the storage used by a resizable array `A` can only grow unless `shrink!(A)` is called to reduce the storage to the minimum. The call `ResizableArray(A)` yields a copy of `A` which is a resizable array.

To improve performances, call `sizehint!(A,n)` to indicate the minimum number of elements to preallocate for `A` (`n` can be a number of elements or array dimensions).

The `ResizableArray` constructor and the `convert` method can be used to convert an array `A` to a resizable array:

```
ResizableArray(A)
convert(ResizableArray, A)
```

If possible, the `convert` method returns the input array while the `ResizableArray` constructor always returns a new instance. Element type `T` and number of dimensions `N` may be specified:

```
ResizableArray{T[,N]}(A)
convert(ResizableArray{T[,N]}, A)
```

`N` must match `ndims(A)` but `T` may be different from `eltype(A)`.

By default, the storage for the elements of a resizable array is provided by a regular Julia vector. To use an object `buf` to store the elements of a resizable array, use one of the following:

```
A = ResizableArray(buf, dims)
A = ResizableArray{T}(buf, dims)
A = ResizableArray{T,N}(buf, dims)
```

The buffer `buf` must store its elements contiguously using linear indexing style with 1-based indices and have element type `T`, that is `IndexStyle(typeof(buf))` and `eltype(buf)` must yield `IndexLinear()` and `T` respectively. The methods, `IndexStyle`, `eltype`, `length`, `getindex` and `setindex!` must be applicable for the type of `buf`. If the method `resize!` is applicable for `buf`, the number of elements of `A` can be augmented; otherwise the maximum number of elements of `A` is `length(buf)`.

!!! warning
    When explicitly providing a resizable buffer `buf` for backing the storage of a resizable array `A`, it is the caller responsibility to make sure that the same buffer is not resized elsewhere. Otherwise a segmentation fault may occur because `A` might assume a wrong buffer size. To avoid this, the best is to make sure that only `A` owns `buf` and only `A` manages its size. In the current implementation, the size of the internal buffer is never automatically reduced so the same buffer may be safely shared by different resizable arrays provided [`shrink!`](@ref) is never called on these arrays.

