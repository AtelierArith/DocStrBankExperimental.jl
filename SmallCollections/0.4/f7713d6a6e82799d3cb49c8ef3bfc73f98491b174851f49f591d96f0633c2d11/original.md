```
MutableFixedVector{N,T} <: AbstractFixedVector{N,T}

MutableFixedVector{N,T}(iter)
MutableFixedVector{N}(iter)
MutableFixedVector(iter)

MutableFixedVector{N,T}(undef)
```

`MutableFixedVector{N,T}` is a mutable vector type that holds exactly `N` elements of type `T`. (It is analogous to `StaticArrays.MVector` and `StaticVectors.Variables`.) The size `N` can be any (small) positive integer. However, at least for bit integer and hardware float types, one usually takes `N` to be a power of `2`.

If the element type `T` or the size `N` are omitted, they are determined from the iterator given as argument. Performance degrades if this is not possible at compile time. As a rule of thumb, the size should only be omitted for `Tuple` arguments.

Note that setting individual vector elements (via `setindex!`) is only supported for `isbits` element types.

The special form `MutableFixedVector{N,T}(undef)` returns a non-initialized vector.

See also [`FixedVector`](@ref), `Base.isbitstype`.
