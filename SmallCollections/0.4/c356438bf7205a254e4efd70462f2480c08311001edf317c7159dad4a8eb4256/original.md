```
bits(v::SmallCollections.AbstractFixedVector{N,T}) where {N, T <: Union{Base.BitInteger,Bool,Char,Enum}} -> Unsigned
```

Convert the given vector to an unsigned integer.

For bit integers, `Char` and `Enum` types this is the same as `reinterpret(U, Tuple(v))` provided that `U` is an unsigned integer type with `N*bitsize(T)` bits, possibly defined by the package `BitIntegers`. Otherwise the result will be zero-extended to the next unsigned integer type `U` whose bit length is a power of `2`.

If the element type is `Bool`, then each element only takes one bit in the return value. If `N` is less than `8` or not a power of `2`, then the result will again be zero-extended.

See also [`SmallCollections.bitsize`](@ref), `Base.BitInteger`, `Base.reinterpret`, `BitIntegers`.

# Examples

```jldoctest
julia> SmallCollections.FixedVector{4,Int8}(1:4) |> bits
0x04030201

julia> SmallCollections.FixedVector{3}('a':'c') |> bits
0x00000000630000006200000061000000

julia> m = SmallCollections.FixedVector{6,UInt32}(1:6) |> bits
0x0000000000000000000000060000000500000004000000030000000200000001

julia> typeof(m)
BitIntegers.UInt256

julia> SmallCollections.FixedVector{22}(map(isodd, 1:22)) |> bits
0x00155555
```
