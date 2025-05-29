```
fasthash(v::AbstractSmallVector [, h0::UInt]) -> UInt
```

Return a hash for `v` that may be computed faster than the standard `hash` for vectors. This new hash is consistent across all `AbstractSmallVector`s of the same element type, but it may not be compatible with `hash` or with `fasthash` for a `AbstractSmallVector` having a different element type.

Currently, `fasthash` differs from `hash` only if the element type of `v` is a bit integer type with at most 32 bits, `Bool` or `Char`.

See also [`fasthash(::PackedVector, ::UInt)`](@ref), `Base.hash`.

# Examples

```jldoctest
julia> v = SmallVector{8,Int8}([1, 5, 6]);

julia> fasthash(v)
0x6466067ab41d0916

julia> fasthash(v) == hash(v)
false

julia> w = SmallVector{16,Int8}(v); fasthash(v) == fasthash(w)
true

julia> w = SmallVector{8,Int16}(v); fasthash(v) == fasthash(w)
false
```
