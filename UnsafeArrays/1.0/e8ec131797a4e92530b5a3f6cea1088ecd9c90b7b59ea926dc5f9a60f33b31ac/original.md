```
UnsafeArray{T,N} <: DenseArray{T,N}
```

An `UnsafeArray` is an bitstype wrapper around a memory pointer and a size tuple. It's an intended to be used as a short-lived, allocation-free alternative to an an `Array` returned by `unsafe_wrap` or a `SubArray` returned by `view` or . Use with caution!

Constructors:

```
UnsafeArray{T,N}(pointer::Ptr{T}, size::NTuple{N,Int}) where {T,N}
UnsafeArray(pointer::Ptr{T}, size::NTuple{N,Int}) where {T,N}
```

UnsafeArray requires `isbitstype(T) == true`.

Note: It's safe to construct an empty multidimensional `UnsafeArray`:

```
UnsafeArray(Ptr{Int}(0), (0,...))
```

Note: You *must* ensure that `A` is not garbage collected or reallocated via (e.g.) `resize!`, `sizehint!` etc. while `U` is in use! Use only in situations where you have full control over the life cycle of `A` and `U`.

`deepcopy(::UnsafeArray)` returns a standard `Array`.
