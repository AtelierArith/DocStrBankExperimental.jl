```
similar_type(static_array)
similar_type(static_array, T)
similar_type(array, ::Size)
similar_type(array, T, ::Size)
```

Returns a constructor for a statically-sized array similar to the input array (or type) `static_array`/`array`, optionally with different element type `T` or size `Size`. If the input `array` is not a `StaticArray` then the `Size` is mandatory.

This differs from `similar()` in that the resulting array type may not be mutable (or define `setindex!()`), and therefore the returned type may need to be *constructed* with its data.

Note that the (optional) size *must* be specified as a static `Size` object (so the compiler can infer the result statically).

New types should define the signature `similar_type(::Type{A},::Type{T},::Size{S}) where {A<:MyType,T,S}` if they wish to overload the default behavior.
