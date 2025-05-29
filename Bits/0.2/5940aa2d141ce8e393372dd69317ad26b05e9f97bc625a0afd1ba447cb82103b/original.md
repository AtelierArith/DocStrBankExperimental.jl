```
mask(T::Type{<:Integer} := UInt, j::Integer, i::Integer) -> T
```

Return an integer of type `T` whose `j` right-most bits are `0`, the following `i-j` bits are `1`, and the remaining bits are `0` (i.e. of the form `0b0...01...10...0` with exactly `i-j` `1`s preceded by `j` `0`s). When `j < 0`, the result is not specified. When `i < 0`, the result is equal to `~mask(T, j)`, i.e. of the form `1...10...0` with exactly `j` zeros. NOTE: unstable API, could be changed to mask(j, i-j) instead.

# Examples

```jldoctest
julia> bits(mask(UInt8, 2, 5))
<00011100>

julia> bits(mask(BigInt, 3, -1))
<...1 11111111 11111111 11111111 11111111 11111111 11111111 11111111 11111000>
```
