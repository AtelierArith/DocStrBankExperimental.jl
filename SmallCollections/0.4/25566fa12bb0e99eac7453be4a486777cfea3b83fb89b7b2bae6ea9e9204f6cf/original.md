```
MutableSmallVector{N,T} <: AbstractSmallVector{N,T}

MutableSmallVector{N,T}()
MutableSmallVector{N,T}(iter)
MutableSmallVector{N}(iter)
MutableSmallVector(v::PackedVector{T})
MutableSmallVector(v::AbstractSmallVector)

MutableSmallVector{N,T}(undef, n::Integer)
```

`MutableSmallVector{N,T}` is a mutable vector type that can hold up to `N` elements of type `T`. It is the mutable analog of `SmallVector{N,T}`.

Note that setting individual vector elements (via `setindex!`) is only supported for `isbits` element types.

The special form `MutableSmallVector{N,T}(undef, n)` returns a non-initialized vector of length `n`.

See also [`SmallVector`](@ref), `Base.isbitstype`.
