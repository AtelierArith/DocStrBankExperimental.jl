```
bitsize(T::Type) -> Int
bitsize(::T)     -> Int
```

Return the number of bits that can be held by type `T`. Only the second method may be defined when the number of bits is a dymanic value, like for `BitFloat`.

# Examples

```jldoctest
julia> bitsize(Int32)  == 32        &&
       bitsize(true)   == 1         &&
       bitsize(big(0)) == Bits.INF  &&
       bitsize(1.2)    == 64
true

julia> x = big(1.2); bitsize(x) == 256 + sizeof(x.exp)*8 + 1
true
```
