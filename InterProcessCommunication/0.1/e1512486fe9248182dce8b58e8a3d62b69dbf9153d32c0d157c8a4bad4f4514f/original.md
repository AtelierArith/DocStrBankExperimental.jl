```julia
WrappedArray(mem, [T [, dims...]]; offset=0)
```

yields a Julia array whose elements are stored in the "memory" object `mem`. Argument `T` is the data type of the elements of the returned array and argument(s) `dims` specify the dimensions of the array.  If `dims` is omitted the result is a vector of maximal length (accounting for the offset and the size of the `mem` object).  If `T` is omitted, `UInt8` is assumed.

Keyword `offset` may be used to specify the address (in bytes) relative to `pointer(mem)` where is stored the first element of the array.

The size of the memory provided by `mem` must be sufficient to store all elements (accounting for the offset) and the alignment of the elements in memory must be a multiple of `Base.datatype_alignment(T)`.

Another possibility is:

```julia
WrappedArray(mem, dec)
```

where `mem` is the "memory" object and `dec` is a function in charge of decoding the array type and layout given the memory object.  The decoder is applied to the memory object as follow:

```julia
dec(mem) -> T, dims, offset
```

which must yield the data type `T` of the array elements, the dimensions `dims` of the array and the offset of the first element relative to `pointer(mem)`.

## Restrictions

The `mem` object must extend the methods `pointer(mem)` and `sizeof(mem)` which must respectively yield the base address of the memory provided by `mem` and the number of available bytes.  Furthermore, this memory is assumed to be available at least until object `mem` is reclaimed by the garbage collector.

## Shared Memory Arrays

```julia
WrappedArray(id, T, dims; perms=0o600, volatile=true)
```

creates a new wrapped array whose elements (and a header) are stored in shared memory identified by `id` (see [`SharedMemory`](@ref) for a description of `id` and for keywords).  To retrieve this array in another process, just do:

```julia
WrappedArray(id; readonly=false)
```

## See Also

[`SharedMemory`](@ref).
