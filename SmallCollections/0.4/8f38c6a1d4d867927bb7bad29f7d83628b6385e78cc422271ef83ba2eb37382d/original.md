```
fasthash(v::PackedVector [, h0::UInt]) -> UInt
```

Return a hash for `v` that may be computed faster than the standard `hash` for vectors. This new hash is consistent across all `PackedVector{U,M,T}` of the same internal bit size `M`, but it may not be compatible with `hash` or with `fasthash` for a `PackedVector` having a different bit size. However, using `fasthash` for two `PackedVector`s with the same `M`, but both signed and unsigned element types `T` may lead to hash collisions.

See also [`fasthash(::AbstractSmallVector, ::UInt)`](@ref), `Base.hash`.

# Examples

```jldoctest
julia> v = PackedVector{UInt64,5,Int8}([1, 5, 6]);

julia> fasthash(v)
0x11e89b9d8f3daac6

julia> fasthash(v) == hash(v)
false

julia> w = PackedVector{UInt128,5,Int8}(v); fasthash(v) == fasthash(w)
true

julia> w = PackedVector{UInt64,4,Int8}(v); fasthash(v) == fasthash(w)
false

julia> w = PackedVector{UInt64,5,UInt8}(v); fasthash(v) == fasthash(w)
true
```
