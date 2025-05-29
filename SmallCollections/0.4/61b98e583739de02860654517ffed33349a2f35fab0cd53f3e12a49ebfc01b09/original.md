```
FixedVector{N,T} <: AbstractFixedVector{N,T}

FixedVector{N,T}(iter)
FixedVector{N}(iter)
FixedVector(iter)
```

`FixedVector{N,T}` is an immutable vector type that holds exactly `N` elements of type `T`. (It is analogous to `StaticArrays.SVector` and `StaticVectors.Values`.) The size `N` can be any (small) positive integer. However, at least for bit integer and hardware float types, one usually takes `N` to be a power of `2`.

If the element type `T` or the size `N` are omitted, they are determined from the iterator given as argument. Performance degrades if this is not possible at compile time. (For tuples, the element type is determined via `promote_type`.) As a rule of thumb, the size should only be omitted for `Tuple` arguments.

See also [`MutableFixedVector`](@ref), `Base.promote_type`.
