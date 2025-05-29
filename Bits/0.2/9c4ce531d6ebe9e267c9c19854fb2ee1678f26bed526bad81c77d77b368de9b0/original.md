```
mask(T::Type{<:Integer}:=UInt, i::Integer=bitsize(T)) -> T
```

Return an integer of type `T` whose `i` right-most bits are `1`, and the others are `0` (i.e. of the form `0b0...01...1` with exactly `i` `1`s. When `i` is not specified, all possible bits are set to `1`. When `i < 0`, the result is not specified. `T` defaults to `UInt`.

# Examples

```jldoctest
julia> mask(3)
0x0000000000000007

julia> mask(UInt8)
0xff

julia> bits(mask(Int32, 24))
<00000000 11111111 11111111 11111111>
```
