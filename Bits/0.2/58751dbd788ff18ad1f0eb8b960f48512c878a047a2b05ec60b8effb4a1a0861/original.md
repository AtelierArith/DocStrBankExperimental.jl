```
bits(x::Real)
```

Create an immutable view on the bits of `x` as a vector of `Bool`, similar to a `BitVector`. If `x` is a `BigInt`, the vector has length [`Bits.INF`](@ref). Currently, no bounds check is performed when indexing into the vector.

# Examples

```jldoctest
julia> v = bits(Int16(2^8+2^4+2+1))
<00000001 00010011>

julia> permutedims([v[i] for i in 8:-1:1])
1×8 Array{Bool,2}:
 false  false  false  true  false  false  true  true

julia> bits(true)
<1>

julia> bits(big(2)^63)
<...0 10000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000>

julia> bits(Float32(-7))
<1|10000001|1100000 00000000 00000000>

julia> ans[1:23] # creates a vector of bits with a specific length
<1100000 00000000 00000000>
```
